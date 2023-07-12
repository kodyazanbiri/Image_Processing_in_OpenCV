# OpenCV İle Resim İçe Aktarma ve Kaydetme
### Kütüphanelerin İçe Aktarılması
```python
import cv2
import time
import numpy as np
import matplotlib.pyplot as plt
```
### Resmi İçe Aktarma Ve Kaydetme
```python

image = cv2.imread("resim1.jpg",0)

cv2.imshow("Ilk resim",image)

key = cv2.waitKey(0) &0xFF   # cv2.waitKey () bir klavye bağlama işlevidir. # İşlev, herhangi bir klavye olayı için belirtilen milisaniye kadar bekler.

if(key==27):                                                  # wait for ESC key to exit
    cv2.destroyAllWindows()                                  # olusturdugumuz tüm pencereleri yok eder.
elif(key== ord("s")):                                       # wait for 's' key to save and exit
     cv2.imwrite("goruntu_isleme/ronaldo_gray.jpg",image)
     cv2.destroyAllWindows()
```
- NOT: `.py` uzantılı dosyamız ile yüklemek istediğimiz fotoğrafın aynı klasörde olması gerekir. Eğer aynı klasörde değilse fotoğrafın olduğu adresi tam olarak yazmalıyız.

-  `“imread()”(image read)` isimli fonksiyon içine yazılan uzantıdaki fotoğrafı içe aktarır. Bu fonksiyon `"resim1.jpg"` isimli bir görüntüyü siyah-beyaz (grayscale) olarak yüklemek ve "Ilk resim" adında bir pencerede görüntülemek için kullanılıyor.

- `cv2.imread("ronaldo.jpg", 0)` komutu, OpenCV kütüphanesini kullanarak "ronaldo.jpg" dosyasını okur. İkinci parametre olan 0, görüntünün siyah-beyaz olarak yüklenmesini sağlar. Eğer 0 yerine 1 veya -1 gibi farklı bir değer verirseniz, renkli olarak yüklenmesini sağlayabilirsiniz.

- `“imshow()”(image show)` fonksiyonuyla ise resmi görselleştirmiş oluyoruz. Bu fonksiyon ilk parametre olarak görselin başlığına yazılacak ismi, ikinci olarak
ise içe aktarılmış resmin eşitlendiği değişkenin ismini alır. Yani "Ilk resim" adında bir pencere oluşturur ve image adlı siyah-beyaz görüntüyü bu pencerede görüntüler.

- `“waitKey()”` fonksiyonu ise klavyeden bir tuşa basılmasını beklemeyi sağlar. İçerisine (1) değeri verilmişse beklemez(tuşa basılmış sayar), (0) değeri verilir
ise tuşa basılmasını bekler. Eğer ki bu fonksiyon olmasaydı resmi biz göremeden hemen açıp kapatır ve göremezdik. Bu tuşa basma işleminden dönen değeri bir
değişkene eşitliyoruz. Daha sonra basılan tuş ile istediğimiz işlemi yapabiliriz. Biz burda ASCII kodu “27” olan (ESC tuşu) tuşana basıldığında tüm pencerelerin
kapatılmasını sağladık. Ayriyeten “ord()” fonksiyonun içine verilen değere basılmışsa (yani bu durumda “s” tuşu oluyor) fotoğrafı kaydetmesini sağladık.
Siyah beyaz olarak yeni bir fotoğraf halinde kaydetmiş olduk. Bu fonksiyon ilk parametre olarak hangi uzantıya kaydedeceğine, ikinci olarak ise hangi fotoğrafı
kaydedeceğini alır.



