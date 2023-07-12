# OpenCV İle Webcam’i Açma Ve Video Kaydetme

```python
import cv2

cap = cv2.VideoCapture(0)

width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

print(width, height) # 640*480=307200 tane piksel var yani çözünürlük değerimiz.

writer = cv2.VideoWriter("goruntu_isleme/self_video.mp4",cv2.VideoWriter_fourcc(*"DIVX"),30,(width,height))

    while True:
        ret,frame = cap.read()

        cv2.imshow("Video",frame)
        writer.write(frame)

        if cv2.waitKey(1) & 0xFF == 27:
            break

cap.release() #stop capture
writer.release()
cv2.destroyAllWindows()

"""
NOT: cv.VideoWriter(filename, fourcc, fps, frameSize)
    dosyaadı: Video dosyası girin
    fourcc: çerçeveleri sıkıştırmak için kullanılan 4 karakterli codec kodu
    fps: video akışının kare hızı
    çerçeve boyutu: Çerçevenin yüksekliği ve genişliği

"""
```
- `“VideoCapture()”` fonksiyonu ile görüntüyü yakalama işlemi yapıyoruz. Bu fonksiyonun içine 0 değeri verilirse birincil kameramızdaki
görüntüyü alacaktır (ikincil bir kamera varsa 1 de yazılabilir). Kameramızın çözünürlük değerini öğrenmek için genişlik ve yükseklik değerlerini
alıyoruz. Bu değerler video kaydederken işimize yarayacak.

- `cap.get(cv2.CAP_PROP_FRAME_WIDTH)` ve `cap.get(cv2.CAP_PROP_FRAME_HEIGHT)` komutları, kameranın çerçeve (frame) genişliğini ve yüksekliğini alır. Bu değerler, kameranın desteklediği maksimum çözünürlüğü temsil eder.

- `“VideoWriter()”` fonksiyonu frameleri bir araya getirerek video oluşmasını sağlar. Bu fonksiyonun parametreleri; videoyu kaydediceği adres,
sıkıştırma algoritması (four_cc çerçeveleri sıkıştırmak için kullanılan 4 karakterli codec kodu), fps(frame per second) değeri ve (genişlik,yükseklik) dir.
`"goruntu_isleme/self_video.mp4"` adında bir video dosyası oluşturup ve bu dosyaya çerçeveleri kaydediyoruz. `cv2.VideoWriter_fourcc(*"DIVX")`: Video sıkıştırma codec'ini belirtir. `"DIVX"` codec'ini kullanarak sıkıştırma yapar. `VideoWriter_fourcc` fonksiyonu, codec'leri dört karakterli bir biçimde temsil eder.
`30: FPS` (çerçeve hızı) değerini belirtir. Bu durumda 30 çerçeve/saniye hızında bir video oluşturulur. `(width, height)`, Çerçeve boyutunu belirtir. Önceden tanımlanan width ve height değerlerini kullanarak çerçeve boyutu ayarlanır.

- Daha sonra webcam den gelen görüntüleri okumaya başlıyoruz. Her bir frame’i hem kullanıcıya gösterirken aynı zamanda da VideoWriter
değişkenimize `“write”` komutu ile frameleri kaydetmesini sağlıyoruz.

- “ESC” tuşuna basılınca bu işlemin biteceğini yazıyoruz. En son videoyu okuma ve yazma işlemini bırakıyoruz. Webcam’imizden aldığımız video kaydedilmiş oluyor.

