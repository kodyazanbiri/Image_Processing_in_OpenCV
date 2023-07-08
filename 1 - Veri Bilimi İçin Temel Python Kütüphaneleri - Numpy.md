# 1 - Veri Bilimi İçin Temel Python Kütüphaneleri - Numpy
NumPy (Numerical Python), dizilerle çalışmak için kullanılan bir Python kütüphanesidir. Doğrusal cebir, fourier dönüşümü ve matrisler alanında çalışmak için de gerekli işlevlere sahiptir. 
Ayrıca bilimsel hesaplamaları hızlı bir şekilde yapmamızı sağlayan bir matematik kütüphanesidir. Numpy’ın temelini numpy dizileri oluşturur. Numpy dizileri
python listelerine benzer fakat hız ve işlevsellik açısından python listelerinden daha kullanışlıdır. Python listelerinden farklı olarak Numpy dizileri homojen yapıda 
olmalıdır yani dizi içindeki tüm elemanlar aynı veri tipinden olmalıdır.



### Neden NumPy Kullanılır?
Python’da dizilerin amacına hizmet eden listelerimiz var, ancak işlenmesi yavaştır. NumPy, geleneksel Python listelerinden 50 kata kadar daha hızlı bir dizi nesnesi sağlamayı amaçlamaktadır. 

### NumPy CodeBase Nerede?
NumPy’nin kaynak kodu bu github deposunda bulunmaktadır. [Bağlantı için tıklayın.](https://github.com/numpy/numpy)

### NumPy’nin Kurulumu
Anaconda, Spyder vb. gibi zaten NumPy’nin kurulu olduğu bir python dağıtımı kullanablirsiniz.

Ya da bir sistemde Python ve PIP kuruluysa NumPy’nin kurulumu çok kolaydır. Bu komutu kullanarak kurulumu yapabilirsiniz.

```python
pip install numpy
```
###  NumPy Sürümünü Kontrol Etme
Sürüm bilgisi version özniteliği altında saklanır.

```python
print(np.__version__)
```
### NumPy’yi Projeye Dahil Etmek
NumPy yüklendikten sonra, `import` anahtar sözcüğünü ekleyerek onu uygulamalarınıza dahil edebilirsiniz.
```python
# Kütüphanemizi np ismi ile import ettik.
import numpy as np
```
Artık NumPy içe aktarılmıştır ve kullanıma hazırdır. 

### Array nesnesi Tanımları
array nesnesi biri zorunlu olmak üzere 6 farklı parametre alır.

|Parametre	  |   Tanımı | 
| --          |:------- | 
|object	      |   Bu dizi şeklinde herhangi bir nesne dizisidir. İç içe geçmiş dizi de içerebilir.|
|dtype	      |   İstenen veri tipi, seçimliktir.|
|copy	        |   object kopyalanır, seçimliktir.|
|order        |   C (ana satır) ya da F (ana kolon) veya A (herhangi biri) (Geçerli değer)|
|subok	      |   Varsayılan olarak, bir temel sınıf array’i olmaya zorlanan diziyi döndürür. Eğer doğruysa, alt sınıflar geçer.|
|ndmin	      |   Sonuç dizisinin minimum boyutlarını belirtir.|

### Numpy dizisinin oluşturulması
Numpy dizisi ve python listesi oluşturup farklarına göz atalım :

```python
# python list
python_list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
# numpy array
numpy_array = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

print("Python listesi :")
print(python_list)
print("Numpy dizisi :")
print(numpy_array)

Output:
Python listesi :
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
Numpy dizisi :
[0 1 2 3 4 5 6 7 8 9]
```
### Dizinin boyutunu bulmak : ndarray.ndim
`.ndim` →numpy array nesnesinin boyutunu döndürür.

```python
numpy_array1 = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
print(numpy_array1.ndim)
Output:
1
numpy_array2 = np.array([[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]])
print(numpy_array2.ndim)
Output:
2
```

### Dizinin satır ve sütun sayısını bulmak: ndarray.shape
`.shape` →Numpy array nesnesinin kaç satır ve sütundan oluştuğunu gösteren bir tupple nesnesi döndürür.

```python
numpy_array1 = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
print(numpy_array1.ndim)
print(numpy_array1.shape)
#10 tane elemandan oluşan 1 boyutlu bir dizi(vektör).
Output:
1
(10,)

numpy_array2 = np.array([[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]])
print(numpy_array2.ndim)
print(numpy_array2.shape)
# 1 satır ve 10 sütundan oluşan 2 boyutlu bir dizi(matris).
Output:
2
(1, 10)

numpy_array3 = np.array([[0, 1, 2] ,[0, 1, 2]])
print(numpy_array3.ndim)
print(numpy_array3.shape)
# 2 satır ve 3 sütundan oluşan 2 boyutlu bir dizi(matris).
Output:
2
(2, 3)
```
### Dizinin satır ve sütun sayısını değiştirmek : ndarray.reshape()
Numpy array’i yeniden şekillendirmek istediğimizde yani satır ve sütun sayısını değiştirmek istediğimizde `reshape()` metodunu kullanabiliriz. numpy_array isimli değişkenimizi yeniden şekillendirelim:

```python
numpy_array = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
print(numpy_array.reshape(1,10))
Output : 
[[0 1 2 3 4 5 6 7 8 9]]
print(numpy_array.reshape(10,1))
Output:
  [[0]  
   [1]
   [2]  
   [3]
   [4]
   [5]  
   [6]  
   [7]
   [8]
   [9]]
print(numpy_array.reshape(5,2))
Output:
  [[0 1]  
   [2 3]
   [4 5]
   [6 7]
   [8 9]]
print(numpy_array.reshape(2,5))
Output:
  [[0 1 2 3 4] 
   [5 6 7 8 9]]
```
### np.arange()
`np.arange()` →Python’daki range() fonksiyonuna benzer. Belirtilen başlangıç değerinden başlayıp, her seferinde adım sayısı kadar arttırarak ,bitiş değerine kadar olan sayıları bulunduran bir numpy dizisi dödürür.

Not: Bitiş değerinin diziye dahil edilmediğine dikkat edelim.

Genel kullanım :

np.arange(başlangıç,bitiş,adım sayısı)

np.arange(bitiş) → bu kullanımda default başlangıç değeri 0 , adım sayısı ise 1 olarak kabul edilir. Yani aslında yukarıda ki formatta ifade edecek olursak np.arange(0,bitiş,1) şeklinde yazabiliriz.

```python
np.arange(0,10,3)
Output:
array([0, 3, 6, 9])

np.arange(10)
Output:
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

np.arange(0,10,1)
Output:
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```
### Dizinin elemanlarını seçmek
`ndarray[:,:]` → buradaki “:” kullanımı tüm satır ve sütunları seçmemizi sağlar.
```python
numpy_array = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
numpy_array = numpy_array.reshape(5,2)
print(numpy_array)
Output:
  [[0 1]  
   [2 3]
   [4 5]
   [6 7]
   [8 9]]
#Dizinin herhangi bir satırını seçmek
#1.satır
first_row = numpy_array[0]
#1. ve 2. satır 
first_and_second_rows = numpy_array[0:2]
print(first_row)
print(first_and_second_rows)
Output:
[0 1]
[[0 1]  [2 3]]
#Dizinin herhangi bir kolonunu seçmek
#1. sütun
first_column = numpy_array[:,0]
#1. ve 2. sütun
first_and_second_column = numpy_array[:,0:2]
print(first_column)
print(first_and_second_column)
Output:
[0 2 4 6 8]
[[0 1] 
 [2 3]
 [4 5] 
 [6 7] 
 [8 9]]
#Dizinin herhangi bir elemanını seçmek
selecting_item = numpy_array[3,1]
print(selecting_item)
Output:
7
```

### Diziyi ters çevirmek
```python
numpy_array = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
numpy_array = numpy_array.reshape(5,2)
print(numpy_array)
Output:
[[0 1] 
 [2 3] 
 [4 5] 
 [6 7] 
 [8 9]]
print(numpy_array[::-1])
Output:
[[8 9]  
 [6 7]
 [4 5] 
 [2 3] 
 [0 1]]
```
