# OpenCV İle Şekil Ve Metin Ekleme
```python
import cv2
import numpy as np

# shape and text
img = np.zeros((512,512,3),np.uint8) # siyah bir resim oluştur # Bunun yerine bir resimde alabiliriz; img = cv2.imread("lenna.png") yazarız
print(img.shape)
cv2.imshow("Image", img)


cv2.line(img, (0,0), (512,512), (0,0,255), 3)
cv2.imshow("Line",img)
cv2.waitKey(0)

cv2.rectangle(img,(300,300), (512,512), (255,0,0),cv2.FILLED)
cv2.imshow("Rectangle",img)
cv2.waitKey(0)

cv2.circle(img,(100,100),45,(0,255,0),10)
cv2.imshow("Circle",img)
cv2.waitKey(0)

cv2.putText(img,"Suna",(300,50),cv2.FONT_HERSHEY_SIMPLEX,0.8,(100,100,100))
cv2.imshow("Metin",img)
cv2.waitKey(0)

k = cv2.waitKey(0) & 0xFF   # Bazı kodlarda hata olmamasına ragmen calistirinca resimler görünmüyor o yüzden bu kod blogunu yazdık.  
if k == 27:         
    cv2.destroyAllWindows()
```
NOT: Normalde renkler RGB (R:red,G:green,B:blue) şeklinde tarif edilir. Fakat OpenCV’de bu tam tersidir. Yani; (255,0,0) kırmızı iken, OpenCV’de (0,0,255) kırmızıdır. Bu renk kombinasyonuna `BGR` denir.

- `np.zeros((512, 512, 3), np.uint8)` ifadesi, np.zeros() fonksiyonunu kullanarak 512x512 piksel boyutunda bir dizi (array) oluşturur. Dizinin her bir elemanı 0 olarak başlatılır. İlk parametre olan (512, 512, 3), oluşturulacak dizinin boyutunu belirtir. Burada 512x512 piksel boyutunda bir resim oluşturmak istediğimiz için bu boyutlar verilir. Son parametre olan 3, resmin üç kanallı (RGB) olacağını belirtir. Her piksel, kırmızı, yeşil ve mavi kanalları içeren bir renk değerini temsil eder.
- İkinci parametre olan  `np.uint8 `, oluşturulan dizinin veri tipini belirtir. np.uint8, 8 bitlik bir işaretli tam sayı veri tipidir ve piksel değerlerini 0-255 aralığında temsil eder.

Sonuç olarak, img adlı değişkene atanmış olan dizi, 512x512 piksel boyutunda, her pikseli siyah renge ([0, 0, 0]) sahip bir resmi temsil eder.

### Çizgi Ekleme

Bir fotoğrafın üstüne çizgi eklemek için “line()” metodu kullanılır. Bu metot parametre olarak; çizgi eklenecek fotoğraf, çizginin başlangıç noktası(x, y koordinatında), çizginin bitiş noktası(x, y koordinatında), BGR renk ve çizgi kalınlığı.

`img` : Çizgiyi çizmek istediğimiz resim.

`(0,0)` : Çizginin başlangıç noktasını temsil eden bir koordinat. Bu durumda, başlangıç noktası (0,0) olarak belirlenmiştir.

`(512,512)` : Çizginin bitiş noktasını temsil eden bir koordinat. Bu durumda, bitiş noktası (512,512) olarak belirlenmiştir.

`(0,255,0)` : Çizgi rengini belirten BGR renk değeri. Bu durumda, çizgi yeşil renkte olacaktır.

`3` : Çizgi kalınlığını belirten bir parametre. Bu durumda, çizgi 3 piksel kalınlığında olacaktır.

### Dörtgen Ekleme

Bir fotoğrafın üstüne dörtgen eklemek için “rectangle()” metodu kullanılır. Bu metot parametre olarak; dörtgen eklenecek fotoğraf, dörtgenin başlangıç noktası(x, y koordinatında), dörtgenin bitiş noktası(x, y koordinatında), BGR renk ve çizgi kalınlığı veya “cv2.FILLED” yazılırsa dörtgenin içini doldurulacağı belirtilir.

`img` : Dikdörtgeni çizmek istediğimiz resim.

`(300,300)` : Dikdörtgenin sol üst köşesini temsil eden bir koordinat. Bu durumda, sol üst köşe (300,300) olarak belirlenmiştir.

`(512,512)` : Dikdörtgenin sağ alt köşesini temsil eden bir koordinat. Bu durumda, sağ alt köşe (512,512) olarak belirlenmiştir.

`(255,0,0)` : Dikdörtgenin kenarlarının renk değerini belirten BGR renk değeri. Bu durumda, kenarlar mavi renkte olacaktır.

`cv2.FILLED`: Dikdörtgenin içini doldurmak için kullanılan bir parametre. Bu durumda, dikdörtgenin içi tamamen doldurulacaktır.

### Daire Ekleme

Bir fotoğrafın üstüne daire eklemek için “circle()” metodu kullanılır. Bu metot parametre olarak; daire eklenecek fotoğraf, dairenin merkez noktası(x, y koordinatında), dairenin yarıçap uzunluğu, BGR renk ve çizgi kalınlığı veya “cv2.FILLED” yazılırsa dörtgenin içini doldurulacağı belirtilir.

`img` : Daireyi çizmek istediğimiz resim.

`(100,100)` : Dairenin merkezini temsil eden bir koordinat. Bu durumda, dairenin merkezi (300,300) olarak belirlenmiştir.

`45` : Dairenin yarıçapını temsil eden bir değer. Bu durumda, dairenin yarıçapı 30 piksel olarak belirlenmiştir.

`(0,255,0)` : Dairenin renk değerini belirten BGR renk değeri. Bu durumda, daire kırmızı renkte olacaktır.

`10` : Dairenin kenarlarının kalınlığını belirler. Daha yüksek bir değer kullanılarak daha kalın bir kenar elde edilebilir veya bunun yerine`cv2.FILLED` : Daireyi doldurmak için kullanılan bir parametredir. Bu durumda, daire tamamen doldurulur. Bu da kullanılabilir.

### Metin Ekleme

Bir fotoğrafın üstüne metin eklemek için “putText()” metodu kullanılır. Bu metot parametre olarak; metin eklenecek fotoğraf, metin, metnin başlangıç noktası(x, y koordinatında), metin fontu, kalınlık ve BGR renk.

`img` : Metni yazdırmak istediğimiz resim.

`"Suna"` : Yazdırılacak metin.

`(300,50)`: Metnin başlangıç noktasını temsil eden bir koordinat. Bu durumda, metin sol üst köşeden (300,50) konumunda başlayacak.

`cv2.FONT_HERSHEY_SIMPLEX` : Kullanılacak yazı tipini belirten bir parametre. Bu durumda, "cv2.FONT_HERSHEY_SIMPLEX" kullanılarak basit bir yazı tipi seçilmiştir.

`0.8` : Metnin ölçeğini belirleyen bir parametre. Bu durumda, metin 0.8 ölçeğinde yazdırılacaktır.

`(100,100,100)` : Metnin renk değerini belirten BGR renk değeri. Bu durumda, metin koyu gri renkte olacaktır.

