# OpenCV İle Perspektif
Eğer iki resimden biri yamuksa, bu durumda benzerlik tabanlı bir algılama yöntemi kullanıyorsanız, yamuk olan resmin düz olan resimle benzer
özelliklere sahip olmadığından algılama başarısız olabilir. Bunun nedeni, benzerlik tabanlı yöntemlerin genellikle desenler, kenarlar, renkler 
veya özellikler gibi resimdeki benzerlikleri temel alan algoritmalardır. Yamuk olan resim, düz olan resimle bu benzerlikleri paylaşmadığından
algılama doğru sonuç vermeyebilir. Bu yüzden perspektif işemini yapmamız gerekebilir.

```python
import cv2
import numpy as np

img = cv2.imread("kart.png")
cv2.imshow("Kart Original",img)
cv2.waitKey(0)

width = 400
height = 500

pts1 = np.float32([[203,1],[1,472],[540,150],[338,617]])
pts2 = np.float32([[0,0],[0,height],[width,0],[width,height]])

matrix = cv2.getPerspectiveTransform(pts1,pts2)

img_perspective = cv2.warpPerspective(img,matrix,(width,height))
cv2.imshow("Kart Perspective",img_perspective)

k = cv2.waitKey(0) & 0xFF   # Bazı kodlarda hata olmamasına ragmen calistirinca resimler görünmüyor o yüzden bu kod blogunu yazdık.  
if k == 27:         
    cv2.destroyAllWindows()
```

- `width = 400` ifadesi, perspektif çarpıtma işleminden sonra elde etmek istediğimiz görüntünün genişliğini belirler. Bu durumda, genişlik değeri 400 olarak atanır.

- `height = 500` ifadesi, perspektif çarpıtma işleminden sonra elde etmek istediğimiz görüntünün yüksekliğini belirler. Bu durumda, yükseklik değeri 500 olarak atanır.

    Bu şekilde, belirli bir görüntüyü yüklerken, perspektif çarpıtma işleminden sonra elde etmek istediğimiz görüntünün genişlik ve yüksekliğini belirleyebiliriz.

- Kartın köşe noktalarını belirlemeliyiz. Bu işlem için fotoğrafı Paint ile açalım. Ve burada imlecimizi kartın köşe noktalarına getirirsek sol altta koordinatları gözükecektir. Bunları not alalım çünkü daha sonra kullanacağız. Bu köşe noktalarını float matrisine çevireceğiz. Bu işlemi Numpy’da bulunan `“float32()”` fonksiyonu ile yapacağız. Sonra bir nokta matrisi daha belirleyeceğiz. Bu matris oluşturmak istediğimiz yeni perspektif uygulanmış fotoğraftaki köşe noktaları olacak. Örneğin; sol üst köşe (0,0) iken , sağ alt köşe yeni oluşturulacak resmin daha önce belirlediğimiz (genişlik, uzunluk) değerleri.

  *  `pts1 ve pts2`, Numpy dizilerini temsil eden nokta koordinatlarını içerir. `pts1` dizisi, orijinal görüntüdeki dört noktanın koordinatlarını içerirken, `pts2` dizisi, perspektif dönüşümü sonucunda elde edilmek istenen görüntüdeki dört noktanın koordinatlarını içerir.

- pts1 ifadesindeki nokta koordinatları şu şekildedir:

  * Nokta 1: (203, 1)
  * Nokta 2: (1, 472)
  * Nokta 3: (540, 150)
  * Nokta 4: (338, 617)

- pts2 ifadesindeki nokta koordinatları ise şu şekildedir:

  * Nokta 1: (0, 0)
  * Nokta 2: (0, height)
  * Nokta 3: (width, 0)
  * Nokta 4: (width, height)
 
- Dönüştürmeyi gerçekleştirmek için perspektif matrisini elde etmemiz gerekiyor. Bunun için `“getPerspectiveTransform()”` fonksiyonu kullanılır. Bu fonksiyon iki nokta matrisini de verdikten sonra 1. noktadan 2. noktaya geçebilmemiz için gerekli olan dönüşüm matrisini verecek. Bu matris (3x3)lük bir matris olacak.

  Şimdi perspektif uygulayabiliriz. Bunun için `“warpPerspective()”` fonksiyonunu kullanıyoruz. Bu fonksiyon bir görüntüye perspektif dönüşümü (perspective transformation) uygulamak için kullanılır. İçerisine parametre olarak; resmi, dönüştürmek için gerekli olan matrisi ve yeni resmin boyutlarını(daha önce belirlediğimiz) alacak.











