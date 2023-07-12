# OpenCV ile Videoyu İçe Aktarma
```python
import cv2
import time

cap = cv2.VideoCapture("video.mp4")

print("Genişlik: ",cap.get(3))      # get fonksiyonun 3.indeksi genişliği verir.
print("Yükseklik: ", cap.get(4))   # get fonksiyonun 4.indeksi yüksekligi verir.
    
if cap.isOpened() == False:
    print("Video aktarılamadı.")

while True:
    ret, frame = cap.read()  # (ret==true ise yani calısıyorsa)burdaki if kısmında frameleri alıp döngüye koyduk yani resimleri alıp ard arda eklemiş ve videoya 
                             # dönüştürmüs olduk.
    if ret == True:
        time.sleep(0.01)
        cv2.imshow("Video",frame)   #frameleri alır, while ile ard arda eklenir
    else:
        break
        
    if cv2.waitKey(1) & 0xFF == 27:
        break
        
cap.release()
cv2.destroyAllWindows() 
```

- Videoyu oynatabilmek için direkt olarak bir görselleştirme metodu kullanamayız. Çünkü, videolar fotoğrafların peş peşe gelmesiyle oluşmakta. Bizde bu
fotoğrafların hızlı bir şekilde peş peşe gelmesini sağlayarak video halinde oynamasını sağlayacağız.

- `“VideoCapture()”` fonksiyonu içine yazılan adresteki videoyu içeri aktarır ve bir değişkene eşitler. Burda `cap` adındaki değişken, cv2.VideoCapture() fonksiyonunu kullanarak video yakalama (capture) nesnesini oluşturur ve belirtilen video dosyasını yükler.

- Videoyu alıp alamadığımı anlamak için videoyu içeri aktarırken eşitlediğimiz değişkeni, `“isOpened()”` fonksiyonuyla kontrol ediyoruz. Video içeri aktarılamamışsa bu değer “False” dönecektir.

- Videolar frame denilen pencerelerden oluşur. `“read()”` fonksiyonu ile bu pencerelerin While döngüsü ile peş peşe alarak görselleştirilmesini
sağlayacağız. Bu “read()” fonksiyonunda 2 değer döner; birinci değer pencerenin alınıp alınmadığı, ikinci değer ise pencerenin kendisi. Birinci değer
“True” ise pencereyi aktarabilmiştir. Bu değer “True” dönerse `“imshow()”` fonksiyonu ile pencereyi görselleştiriyoruz.

  NOT: Frame; videonun içinde bulunan her bir resimdir. ret; işlemin basarılı olup olmadığıdır. Eğer cap.read() fonk basarısız olursa false degerini döndürür. 

- While döngüsü sürekli dönerek video bitene kadar pencerelerin peş peşe görselleştirilmesini, yani pencerelerin video halinde görünmesini sağlar.
Time modülündeki `“sleep()“` fonksiyonunu kullanarak pencerelerin daha yavaş görselleştirilmesini sağlıyoruz. Bunu yapmaz isek videomuz çok hızlanır.

- “ESC” tuşuna basıldığında videodan çıkılmasını sağlıyoruz. Bunu yapmaz isek videoyu kapatmakta sıkıntılar çıkabiliyor. Son olarak da video çekme işlemini `“release()”` fonksiyonu ile bırakıyoruz.
