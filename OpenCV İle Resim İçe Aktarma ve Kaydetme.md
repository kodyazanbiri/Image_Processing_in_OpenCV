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

key = cv2.waitKey(0) &0xFF

if(key==27):
    cv2.destroyAllWindows()
elif(key== ord("s")):
     cv2.imwrite("goruntu_isleme/ronaldo_gray.jpg",image)
     cv2.destroyAllWindows()
```
- .py uzantılı dosyamız ile yüklemek istediğimiz fotoğrafın aynı klasörde olması gerekir. Eğer aynı klasörde değilse fotoğrafın olduğu adresi tam olarak yazmalıyız.

- OpenCV kütüphanesinde `“imread()”(image read)` isimli bir fonksiyon bulunmakta. Bu fonksiyon içine yazılan uzantıdaki fotoğrafı içe aktarır.
Fonksiyonun içine “0” değerli bir parametre daha gönderdiğim için resmi siyah beyaz olarak içe aktardı. Bu parametre yerine bir şey yazmazsanız normal renklerinde aktarır.

- `“imshow()”(image show)` fonksiyonuyla ise resmi görselleştirmiş oluyoruz. Bu fonksiyon ilk parametre olarak görselin başlığına yazılacak ismi, ikinci olarak
ise içe aktarılmış resmin eşitlendiği değişkenin ismini alır.

- `“waitKey()”` fonksiyonu ise klavyeden bir tuşa basılmasını beklemeyi sağlar. İçerisine (1) değeri verilmişse beklemez(tuşa basılmış sayar), (0) değeri verilir
ise tuşa basılmasını bekler. Eğer ki bu fonksiyon olmasaydı resmi biz göremeden hemen açıp kapatır ve göremezdik. Bu tuşa basma işleminden dönen değeri bir
değişkene eşitliyoruz. Daha sonra basılan tuş ile istediğimiz işlemi yapabiliriz. Biz burda ASCII kodu “27” olan (ESC tuşu) tuşana basıldığında tüm pencerelerin
kapatılmasını sağladık. Ayriyeten “ord()” fonksiyonun içine verilen değere basılmışsa (yani bu durumda “s” tuşu oluyor) fotoğrafı kaydetmesini sağladık.
Siyah beyaz olarak yeni bir fotoğraf halinde kaydetmiş olduk. Bu fonksiyon ilk parametre olarak hangi uzantıya kaydedeceğine, ikinci olarak ise hangi fotoğrafı
kaydedeceğini alır.



