# OpenCV ile Resim Yeniden Boyutlandırma Ve Kırpma
```python
import cv2

img = cv2.imread("lenna.png")
print("Resim boyutu: ", img.shape)
cv2.imshow("Lenna_orjinal",img)
cv2.waitKey(0)

img_resized = cv2.resize(img,(800,800))
cv2.imshow("Lenna Resized",img_resized)
cv2.waitKey(0)

img_cropped = img[150:450,100:400]
cv2.imshow("Lenna Cropped",img_cropped)
cv2.waitKey(0)
```

- Fotoğrafları yeniden boyutlandırmak için OpenCV bu konuda en iyi kütüphane oluyor. Bu işlem için `“resize()”`
fonksiyonunu kullanıyoruz. Bu fonksiyon ilk parametre olarak boyutlandırma işleminin hangi fotoğrafa uygulanacağını, ikinci olarak ise yeniden boyutlandırmak
 istediğimiz genişlik ve yükseklik değerlerini alıyor. Genişlik ve yükseklik değerini tuple olarak almakta.

- Fotoğraflar aslında birer 2 boyutlu matristir. Dolayısıyla bu matris indeksleri arasında belirli seçimler yapılarak kırpma işlemi gerçekleştirilir. Bunun
için bir fonksiyona ihtiyaç duymamaktayız. Bir matrise, köşeli parantez içerisinde verdiğimiz değerler ile sadece istediğimiz indekslerin görüntülenmesini
sağlayabiliriz. Bu işlemde “150:450” değeri satırdan(genişlik) 150. indeksten 450. indekse kadar göster, sütundan(yükseklik) da “100:400” değeri 100. indeksten 400. indekse kadar göster demek anlamına geliyor. Bu değerler istenilen şekilde değiştirebilerek kırpma işlemi gerçekleştirilir.
