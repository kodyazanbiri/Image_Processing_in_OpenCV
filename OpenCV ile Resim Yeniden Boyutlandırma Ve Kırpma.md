# OpenCV ile Resim Yeniden Boyutlandırma Ve Kırpma
```python

import cv2

img = cv2.imread("lenna.png")
print("Resim boyutu: ", img.shape)
cv2.imshow("Lenna_orjinal",img)
cv2.waitKey(0)

# yeniden boyutlandırma
img_resized = cv2.resize(img,(800,800))
cv2.imshow("Lenna Resized",img_resized)
cv2.waitKey(0)

# kırpma işlemi
img_cropped = img[150:450,100:400]
cv2.imshow("Lenna Cropped",img_cropped)
cv2.waitKey(0)


k = cv2.waitKey(0) & 0xFF   # Bazı kodlarda hata olmamasına ragmen calistirinca resimler görünmüyor o yüzden bu kod blogunu yazdık.  
if k == 27:         
    cv2.destroyAllWindows()

```

- Fotoğrafları yeniden boyutlandırmak için OpenCV bu konuda en iyi kütüphane oluyor. Bu işlem için `“resize()”`
fonksiyonunu kullanıyoruz. Bu fonksiyon ilk parametre olarak boyutlandırma işleminin hangi fotoğrafa uygulanacağını, ikinci olarak ise yeniden boyutlandırmak istediğimiz genişlik ve yükseklik değerlerini alıyor. Genişlik ve yükseklik değerini tuple olarak almakta.

- `cv2.waitKey(0)` komutu, kullanıcının bir tuşa basana kadar beklemesini sağlar. Yani sıfıra basılmadan bir sonraki resim açılmıyor. Bu örnekte toplam 3 adet resim oluşur.
- Fotoğraflar aslında birer 2 boyutlu matristir. Dolayısıyla bu matris indeksleri arasında belirli seçimler yapılarak kırpma işlemi gerçekleştirilir. Bunun
için bir fonksiyona ihtiyaç duymamaktayız. Bir matrise, köşeli parantez içerisinde verdiğimiz değerler ile sadece istediğimiz indekslerin görüntülenmesini
sağlayabiliriz. `img[150:450,100:400]` ifadesi, iki boyutlu bir dilimleme işlemidir. İlk indeksler 150'dan başlar ve 450'e kadar (450 dahil değil) olan aralığı seçer. İlk indeksler, resmin yükseklik (satır) boyutunu belirtir. İkinci indeksler ise 100'den başlar ve 400'e kadar olan aralığı seçer. İkinci indeksler, resmin genişlik (sütun) boyutunu belirtir. Bu dilimleme işlemi sonucunda, seçilen bölge 300x300 piksel boyutunda olacaktır. Bu değerler istenilen şekilde değiştirebilerek kırpma işlemi gerçekleştirilir.
