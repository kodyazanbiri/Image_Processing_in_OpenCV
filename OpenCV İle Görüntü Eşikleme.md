# OpenCV İle Görüntü Eşikleme
```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread("img1.JPG")
img = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)

plt.figure(), plt.imshow(img,cmap="gray"), plt.axis("off"), plt.title("Original Image"), plt.show()  # Bunları alt altada yazabilirdik.

_,thresh_img = cv2.threshold(img,thresh=60,maxval=255,type=cv2.THRESH_BINARY)
plt.figure(),plt.imshow(thresh_img,cmap="gray"),plt.axis("off"),plt.title("thresh_img"),plt.show()

_,thresh_img_inverse = cv2.threshold(img,thresh=60,maxval=255,type=cv2.THRESH_BINARY_INV)
plt.figure(),plt.imshow(thresh_img_inverse,cmap="gray"),plt.axis("off"),plt.title("thresh_img_inverse"),plt.show()

thresh_img2 = cv2.adaptiveThreshold(img,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,8)
plt.figure(),plt.imshow(thresh_img2,cmap="gray"),plt.axis("off"),plt.title("adaptiveThreshold"),plt.show()

"""
Parametreler
    src Kaynak 8 bitlik tek kanallı görüntü.
    dst Aynı boyutta ve src ile aynı tipte hedef görüntüsü.
    maxValue Koşulun karşılandığı piksellere atanan sıfır olmayan değer
    adaptiveMethod Kullanılacak uyarlanabilir eşikleme algoritması, bkz. AdaptiveThresholdTypes. BORDER_REPLICATE | BORDER_ISOLATED, sınırları işlemek için kullanılır.
    THRESH_BINARY veya THRESH_BINARY_INV olması gereken eşik türü Eşikleme türü, bkz. Eşik Türleri.
    blockSize Piksel için bir eşik değeri hesaplamak için kullanılan bir piksel mahallesinin boyutu: 3, 5, 7, vb.
    C Sabit, ortalamadan veya ağırlıklı ortalamadan çıkarılır (aşağıdaki ayrıntılara bakın). Normalde pozitiftir ancak sıfır veya negatif de olabilir.
"""
"""
Önceki bölümde eşik değer olarak global bir değer kullandık. 
Ancak görüntünün farklı alanlarda farklı aydınlatma koşullarına sahip olduğu tüm koşullarda iyi olmayabilir.
Bu durumda, uyarlamalı eşiklemeye gidiyoruz. 
Bunda, algoritma görüntünün küçük bir bölgesi için eşiği hesaplar. 
böylece aynı görüntünün farklı bölgeleri için farklı eşikler elde ederiz ve 
bu bize farklı aydınlatmaya sahip görüntüler için daha iyi sonuçlar verir.
"""

```
- Görüntü eşiklemeye geçmeden önce fotoğrafımızı siyah beyaz olarak içe aktarmak isteriz. Çünkü diğer türlü eşikleme sonrasında oluşan renklerin
 pek anlamı olmamakta. Bu işlemi ya fotoğrafı içe aktarırken yanında `“0”` parametresini de göndermek `(“img = cv2.imread(“img1.JPG”,0)”)` , ya
da OpenCV içinde bulunan `“cvtColor()”(convertColor)` fonksiyonunu kullanarak yapabiliriz. Bu fonksiyon görüntünün renk kombinasyonunu değiştirir.
Görüntüler OpenCV’ye BGR formatında gelir. Bu yüzden siyah beyaza çevirmek için `“cv2.COLOR_BGR2GRAY”` fonksiyonunu
kullanabiliriz. İstenirse `“cv2.COLOR_BGR2RGB”` ile de renkler normal bildiğimiz renk kombinasyonuna çevrilebilir.

- `cv2.threshold işlevi` : Bir görüntüyü belirli bir eşik değeriyle karşılaştırarak pikselleri iki farklı değere dönüştürür. Bu dönüşüm, verilen eşik değerine göre piksellerin siyah (0) veya beyaz (255) olarak ayarlanmasıyla gerçekleştirilir.

  * `img`: İşlenmek üzere verilen orijinal görüntü.
  * `thresh`: Eşik değeri. Bu değere göre pikseller karşılaştırılır ve ikili dönüşüm gerçekleştirilir.
  * `maxval`: Eşikleme sonrası beyaz piksellerin değeri. Burada, beyaz için 255 (maksimum değer) olarak ayarlanır.
  * `type`: Eşikleme yöntemi türü. Burada, cv2.THRESH_BINARY kullanılır, bu da eşik değeri üzerindeki pikselleri beyaz, altındaki pikselleri siyah olarak ayarlar.

- Threshold değerini neye göre belirlediğimizi anlamak için matplotlib kütüphanesinden yararlanabiliriz. Bu kütüphane bize çok iyi görüntüleme
fonksiyonları sunmakta. Biz bu yazıda `“pyplot()”` fonksiyonundan yararlanacağız. Bu fonksiyonu başta da dahil ederken görüldüğü üzere `“plt”` ismiyle
kaydetmiştik. Öncelikle `“plt.figure()”` yazarak bir görüntü oluşturacağımızı söylüyoruz. Daha sonra `“plt.imshow()”` görüntülenecek
görüntü, `“plt.axis(“off”)” ` diyerek eksenlerden kurtulma, `“plt.title()”` görüntüye başlık verme ve son olarakta `“plt.show()”` diyerek görüntüyü
kullanıcıya göstermiş oluyoruz. plt.imshow()’un içinde bulunan “cmap” parametresine “gray” vererek resmi siyah beyaz göstermeyi sağlıyoruz.

- Bu görüntüleme işlemi tamamlandığında imleci fotoğrafın üzerinde gezdirerek o imlecin altındaki pikselin renk skalasında nerede olduğunu 
gösteriyor. Örneğin kırmızı bölge 10 iken, mavi bölge 214 çıkıyor. Siyah beyaz skalada koyular en düşük olanlardır. Bizde koyu olan yerleri 
yani ağacı göstermek istediğimiz için threshold fonksiyonundaki `“thresh”` değerini buna göre belirliyoruz.

- Eşikleme(thresholding) işlemine gelirsek, bu işlem için `“threshold()”` fonksiyonu bulunmakta. Bu fonksiyon 2 değer dönmekte ama 1. değer işimize
yaramayacağı için onu boş bir değişkene`(“_” gibi)` eşitliyoruz. 2. değişken ise elde etmek istediğimiz eşiklenmiş görüntü olacak. Bu fonksiyon 
içerisine parametre olarak; işlem yapılmak istenen görüntü, thresh = bu fonksiyon için 60’ın üzerinde kalan yerleri görmek istiyorum 
demek , maxval = 60 ile 255 arasında kalan yerleri göstermeyecektir ve type = nasıl bir dönüşüm yapılması istendiği değerlerini alır. 
Bu type değişkeni `“cv2.THRESH_BINARY”` verilirse 60 ile 255 arasını beyaz yaparken diğer kalan yerleri siyah yapar. `“cv2.THRESH_BINARY_INV”` ise
tam tersi olarak 60 ile 255 arasını siyah, kalanları beyaz yapar.

- Adaptive Threshold ise uyarlanabilir eşiktir. Bu fonksiyon kendi otomatik olarak ayarlamaya çalışır. İstenirse bu da kullanılabilir.
`“adaptiveThreshold()”` fonksiyonu parametre olarak; işlenecek görüntü, `maxval(255 verilir genelde)`, `“cv2.ADAPTIVE_THRESH_MEAN_C”` adaptive threshold 
fonksiyonu, 11 değeri blok boyutudur ve 8 ise C sabiti(değiştirilmemesi önerilir) değerlerini alır.

