# OpenCV İle Görüntülerin Birleştirilmesi
```python
import cv2
import numpy as np

img = cv2.imread("lenna.png")
cv2.imshow("Lenna",img)
cv2.waitKey(0)

hor = np.hstack((img,img)) #yatayda birleştirmek için
cv2.imshow("Horizontal Lenna",hor)
cv2.waitKey(0)

ver = np.vstack((img,img)) # dikeyde birleştirmek için
cv2.imshow("Vertical Lenna",ver)
cv2.waitKey(0)

k = cv2.waitKey(0) & 0xFF   # Bazı kodlarda hata olmamasına ragmen calistirinca resimler görünmüyor o yüzden bu kod blogunu yazdık.  
if k == 27:         
    cv2.destroyAllWindows()
```
- Bazı durumlarda dikey veya yatay olarak resimleri yan yana getirmek isteyebiliriz. Bunun için Numpy’da iki fonksiyon bulunmakta. Resimler matristen oluştuğu için Numpy bu matrisleri sütun veya satır bazlı birleştirme yapabilir.

- `“hstack()”` Numpy içerisinde bulunan bu fonksiyon, içine girilen matrislerin sütunlarını birleştirir. Yani fotoğrafları yatay bir şekilde birleştirmekte. Bu fonksiyonu kullanmak için içerisinde `tuple` şeklinde iki resmi atmamız yeterli olacaktır.

- `“vstack()”` fonksiyonu ise “hstack()” ile aynı çalışır. Tek farkı yatay değil, dikey şekilde birleştirmesidir. Matris şeklinde bakarsak satırları birleştirir.
