# OpenCV İle Görüntüleri Karıştırma
```python
import cv2
import matplotlib.pyplot as plt

# blending
img1 = cv2.imread("img1.jpg")
img1= cv2.cvtColor(img1, cv2.COLOR_BGR2RGB) # BGR renk modelinden RGB renk modeline dönüşür.
img2 = cv2.imread("img2.jpg")
img2 = cv2.cvtColor(img2, cv2.COLOR_BGR2RGB)

#resmi görselleştirelim
plt.figure()
plt.imshow(img1)

plt.figure()
plt.imshow(img2)

print(img1.shape)
print(img2.shape)

img1 = cv2.resize(img1,(600,600))
print(img1.shape)

img2 = cv2.resize(img2,(600,600))
print(img1.shape)

plt.figure() 
plt.imshow(img1)

plt.figure()
plt.imshow(img2)

# blended = alpha*img1 + beta*img2 + gamma
blended = cv2.addWeighted(src1=img1, alpha = 0.3, src2=img2,beta=0.7, gamma = 0)
plt.figure()
plt.imshow(blended)

```
- Görselleştirmek için matplotlib kütüphanesini kullanıcaz. OpenCV'de kullanılan renkler BGR (Mavi, Yeşil, Kırmızı) renk modeline dayanır. Fakat resimleri
yüklediğimizde default olarak RGB olarak yüklenir. Bu renkleri düzenlemek için `cvtColor(img1, cv2.COLOR_BGR2RGB)` ve `cvtColor(img2, cv2.COLOR_BGR2RGB)`
fonksiyonlarını kullandık.
- Dikkat edilmesi gereken en önemli şey, karıştırılmak istenen fotoğrafların birbirleriyle aynı boyutta olmaları gerektiği. Bu yüzden öncelikle 2 fotoğrafı da istenilen herhangi bir boyuta getiriyoruz. `cv2.resize(img1,(600,600)` ve `cv2.resize(img2,(600,600)` şeklinde yazıp boyutları eşitledik.
- Daha sonra `“addWeighted()”` fonksiyonu ile resimleri karıştırma işlemi yapıyoruz. Bu fonksiyon parametre olarak; src1 = ilk fotoğraf, src2 = ikinci fotoğraf, alpha = bu değer ilk fotoğrafın yüzde kaç oranda karıştırılacağı, beta = ikinci fotoğrafın yüzde kaç oranda karıştırılacağı ve gamma = ışık efekti sağlar(kontrastı arttırır) değerlerini alır.






