# OpenCV İle Şekil Ve Metin Ekleme
```python
img = cv2.imread("lenna.png")
cv2.imshow("Original",img)
cv2.waitKey(0)

cv2.line(img, (0,0), (512,512), (0,0,255), 3)
cv2.imshow("Line",img)
cv2.waitKey(0)

cv2.rectangle(img,(300,300), (512,512), (255,0,0),cv2.FILLED)
cv2.imshow("Rectangle",img)
cv2.waitKey(0)

cv2.circle(img,(100,100),45,(0,255,0),10)
cv2.imshow("Circle",img)
cv2.waitKey(0)

cv2.putText(img,"Omer Senol",(300,50),cv2.FONT_HERSHEY_SIMPLEX,0.8,(100,100,100))
cv2.imshow("Metin",img)
cv2.waitKey(0)
```
Başlamadan önce, normalde renkler RGB (R:red,G:green,B:blue) şeklinde tarif edilir. Fakat OpenCV’de bu tam tersidir. Yani; (255,0,0) kırmızı iken, OpenCV’de (0,0,255) kırmızıdır. Bu renk kombinasyonuna BGR denir. Bu yüzden renk verilirken bu durum unutulmamalı.

### Çizgi Ekleme

Bir fotoğrafın üstüne çizgi eklemek için “line()” metodu kullanılır. Bu metot parametre olarak; çizgi eklenecek fotoğraf, çizginin başlangıç noktası(x, y koordinatında), çizginin bitiş noktası(x, y koordinatında), BGR renk ve çizgi kalınlığı.

### Dörtgen Ekleme

Bir fotoğrafın üstüne dörtgen eklemek için “rectangle()” metodu kullanılır. Bu metot parametre olarak; dörtgen eklenecek fotoğraf, dörtgenin başlangıç noktası(x, y koordinatında), dörtgenin bitiş noktası(x, y koordinatında), BGR renk ve çizgi kalınlığı veya “cv2.FILLED” yazılırsa dörtgenin içini doldurulacağı belirtilir.

### Daire Ekleme

Bir fotoğrafın üstüne daire eklemek için “circle()” metodu kullanılır. Bu metot parametre olarak; daire eklenecek fotoğraf, dairenin merkez noktası(x, y koordinatında), dairenin yarıçap uzunluğu, BGR renk ve çizgi kalınlığı veya “cv2.FILLED” yazılırsa dörtgenin içini doldurulacağı belirtilir.

### Metin Ekleme

Bir fotoğrafın üstüne metin eklemek için “putText()” metodu kullanılır. Bu metot parametre olarak; metin eklenecek fotoğraf, metin, metnin başlangıç noktası(x, y koordinatında), metin fontu, kalınlık ve BGR renk.

