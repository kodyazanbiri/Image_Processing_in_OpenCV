# OpenCV İle Bulanıklaştırma
```python
img = cv2.imread("NYC.jpg")
img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
plt.figure(),plt.imshow(img),plt.axis("off"),plt.title("original"),plt.show()

mean_blur =cv2.blur(img,ksize=(3,3))
plt.figure(),plt.imshow(mean_blur),plt.axis("off"),plt.title("mean_bluring"),plt.show()

gb =cv2.GaussianBlur(img,ksize=(3,3),sigmaX=7)
plt.figure(),plt.imshow(gb),plt.axis("off"),plt.title("gaussian_bluring"),plt.show()

median_blur =cv2.medianBlur(img,ksize=3)
plt.figure(),plt.imshow(median_blur),plt.axis("off"),plt.title("median_bluring"),plt.show()
```
Bulanıklaştırma işlemini yapmak istememizin en büyük nedenlerinden biri görüntüdeki gürültüyü azaltmaktır. Fakat unutulmaması gereken bir kötü yanı vardır ki, detaylardan feragat etmemiz gerektiği. Öncelikle fotoğrafımızı içe aktarırken renk dönüşümü yapalım. Fotoğrafı BGR renk skalasından, RGB renk skalasına dönüştürelim. OpenCV’de bulanıklaştırmak için birden fazla yol bulunmakta.

Birinci yol olarak Ortalama Bulanıklaştırma yöntemini ele alalım. Bu işlemi, görüntünün normalleştirilmiş bir kutu filtresiyle sarılmasıyla yapıyor. Yani 5x5 piksellik bir kutu düşünelim, bu kutu resmin her pikselinde tek tek dolaştığını ve bu dolaşma sırasında üzerine geldiği piksellerin ortalamasını alarak oraya uyguluyor ve bu sayede bulanıklık sağlıyor. Eğer o piksellerde gürültü varsa, normal pikseller gürültüye baskın olacağı için gürültü ortadan kalkmış oluyor. Bu işlem “blur()” fonksiyonu ile yapılıyor. Bu fonksiyon sadece resmin kendisini ve kutunun boyutunu alıyor.

İkinci bir yol olarak Gauss Bulanıklaştırması var. Bu fonksiyon kutu filtresi yerine Gauss çekirdeği kullanır. Bu çekirdek yine kutu mantığında fakat içerisindeki değerler farklı. Gauss çekirdeğinin içerisinde sigmalar vardır. X ve Y yönlerindeki sigmaları belirtilerek Gauss çekirdeği oluşturulur. Bu çekirdek yapısı aynı şekilde resmin üzerinde dolaşır, fakat ortalama değeri almak yerine çekirdeğin içerisinde bulunan bizim daha önce belirlediğimiz değerlere göre işlem yapar. Bu işlem için “GaussianBlur()” fonksiyonu kullanılır. Bu fonksiyon içerisine işlenecek görüntü, çekirdek boyutu ve sigma değerini alır. Biz burada SigmaY değerini verdik, Kendisi SigmaX değerini bulacaktır.

Anlatacağım son yol Medyan Bulanıklaştırma. Bu fonksiyon ortalama bulanıklaştırma ile neredeyse birebir aynı çalışmakta. Tek farkı üzerinde olduğu piksellerin ortalamasını almak yerine medyan değerini alarak bulanıklık sağlıyor. Salt-and-pepper noise(tuz-biber gürültüsü) dediğimiz gürültüye karşı çok etkili bir bulanıklaştırma metotudur. “medianBlur()” fonksiyonu içerisine sadece görüntü ve kutu boyutunu almakta.

### Gürültü Ekleme
?? ekle





