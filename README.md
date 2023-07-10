# OpenCV ile Videoyu İçe Aktarma
```python
cap = cv2.VideoCapture("video.mp4")
    
if cap.isOpened() == False:
    print("Video aktarılamadı.")

while True:
    ret, frame = cap.read()

    if ret == True:
        time.sleep(0.01)
        cv2.imshow("Video",frame)   
    else:
        break
        
    if cv2.waitKey(1) & 0xFF == 27:
        break
        
cap.release()
```

- Videoyu oynatabilmek için direkt olarak bir görselleştirme metodu kullanamayız. Çünkü, videolar fotoğrafların peş peşe gelmesiyle oluşmakta. Bizde bu
fotoğrafların hızlı bir şekilde peş peşe gelmesini sağlayarak video halinde oynamasını sağlayacağız. `“VideoCapture()”` fonksiyonu içine yazılan adresteki
videoyu içeri aktarır ve bir değişkene eşitler.

- Videoyu alıp alamadığımı anlamak için videoyu içeri aktarırken eşitlediğimiz değişkeni, `“isOpened()”` fonksiyonuyla kontrol ediyoruz. Video içeri aktarılamamışsa bu değer “False” dönecektir.

- Videolar frame denilen pencerelerden oluşur. `“read()”` fonksiyonu ile bu pencerelerin While döngüsü ile peş peşe alarak görselleştirilmesini
sağlayacağız. Bu “read()” fonksiyonunda 2 değer döner; birinci değer pencerenin alınıp alınmadığı, ikinci değer ise pencerenin kendisi. Birinci değer
“True” ise pencereyi aktarabilmiştir. Bu değer “True” dönerse `“imshow()”` fonksiyonu ile pencereyi görselleştiriyoruz.

- While döngüsü sürekli dönerek video bitene kadar pencerelerin peş peşe görselleştirilmesini, yani pencerelerin video halinde görünmesini sağlar.
Time modülündeki `“sleep()“` fonksiyonunu kullanarak pencerelerin daha yavaş görselleştirilmesini sağlıyoruz. Bunu yapmaz isek videomuz çok hızlanır.

- “ESC” tuşuna basıldığında videodan çıkılmasını sağlıyoruz. Bunu yapmaz isek videoyu kapatmakta sıkıntılar çıkabiliyor. Son olarak da video çekme işlemini `“release()”` fonksiyonu ile bırakıyoruz.
