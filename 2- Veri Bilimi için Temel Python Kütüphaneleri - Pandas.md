# 2- Veri Bilimi için Temel Python Kütüphaneleri - Pandas
Veri bilimcilerinin en fazla zamanlarını alan aşama veri ön işleme ve veri temizlemedir. Pandas kütüphanesi ile veri organize edilerek analizler
daha kolay ve hızlı yapılır. 

- Pandas sayısal hesaplamalar için NumPy ve SciPy gibi kütüphaneleri ve veriyi görselleştirmek için Matplotlib kütüphanesini kullanır.
- Pandas’ın NumPy’daki metotlara benzer metotları vardır. NumPy aynı veri tipleri ile çalışırken Pandas farklı veri tipleri ile de çalışabilir. Excelde yazılmış bir veri seti ya da bir SQL tablosu verisi, Pandas ile kolayca analiz edilebilir.

### Pandas Nasıl Yüklenir?
Veri analizi için gerekli kütüphaneleri yüklemenin en kolay yolu Anaconda platformunu kullanmaktır. Anaconda ücretsiz bir platformdur ve 
Anaconda ile Pandas, NumPy, Matplotlib, Scikit-Learn gibi önemli kütüphaneler yüklü olarak gelir. 

- Anaconda kullanmadan Pandas’ı yüklemek isterseniz pip komutunu kullanabilirsiniz. 
```python
pip install pandas
```
- Pandas kütüphanesini yükledikten sonra kullanmak için import etmek gerekir.
```python
import pandas as pd
```
- Pandasın bilgisayardaki yüklü versiyonunu görmek için;
```python
pd.__version__
```
## Pandas veri yapıları
### 1. Series
### 2. DataFrames
DataFrame veri yapısı iki boyutludur yani satırlar ve sütunlardan oluşur.

### 1. Seriler(Series)
Seriler Numpy dizileri baz alınarak oluşturulmuştur. Dolayısıyla tek boyutlu Numpy dizilerine çok benzerler yani bir boyutludur ve bir sütundan oluşur.

Serilerin genel kullanımı :
```python
my_series = pd.Series(data,index)
```
şeklindedir.

- Burada data parametresi
  * sabit bir değer,
  * liste,
  * Numpy dizisi veya
  * bir dictionary

 olabilir. Öncelikle bir Numpy dizisi ve bir Pandas serisi oluşturup farklarına ve benzerliklerine göz atalım.

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
numpy_array = np.array(numbers)
print(numpy_array)
Output :
[0 1 2 3 4 5 6 7 8 9]
pandas_series = pd.Series(data=numbers)
print(pandas_series)
Output :
0    0
1    1
2    2
3    3
4    4
5    5
6    6
7    7
8    8
9    9
dtype: int64
```
- Numpy dizisinden farklı olarak serilerde index sütunu da bulunur. İndex sütunu belirtilmediği takdirde default olarak n uzunlukta bir dizi için 0'dan başlayıp 1,2,… şeklinde (n-1)’e kadar devam eden bir dizi olur.
```python
my_index = ['a', 'b', 'c', 'd', 'e', 'f', 'g','h', 'i','j']
pandas_series = pd.Series(data=numbers, index=my_index, dtype=float)
print(pandas_series)
Output : 
a    0.0
b    1.0
c    2.0
d    3.0
e    4.0
f    5.0
g    6.0
h    7.0
i    8.0
j    9.0
dtype: float64
```
Yukarıda default index yerine kendi belirlediğimiz “my_index” listesini kullandık. Burada dikkat edilmesi gereken nokta dizinin uzunluğu ile tanımlanan index listesinin uzunluğunun eşit olmasıdır. Ayrıca serinin veri tipini float olarak belirledik. Çıktı kısmına baktığımızda da dtype: float64 olduğunu görebiliyoruz.

```python
numbers_dictionary = {'a': 0, 'b':1, 'c':2, 'd':3, 'e':4, 'f':5, 'g':6,'h':7, 'i':8,'j':9}
pandas_series = pd.Series(data=numbers_dictionary)
print(pandas_series)
Output :
a    0
b    1
c    2
d    3
e    4
f    5
g    6
h    7
i    8
j    9
dtype: int64
```
Serinin data parametresi bir dictionary olduğunda ‘key’ kısımlarının index olarak kullanıldığını görebilirsiniz.

Seriler Numpy dizilerine çok benzer. Bu sebeple Numpy dizilerine ait bir çok fonksiyon ve metot seriler için de geçerlidir. Öyleyse Numpy dizilerinde ne gibi işlemler yaptığımızı hatırlayalım. Daha detaylı bilgi için Numpy ile ilgili yazıma göz atabilirsiniz.

- ndim, dtype, shape.. gibi özellikleri seriyi incelemek için Pandas’ta da kullanabiliyoruz.
```python
print(pandas_series.ndim)
Output :
1
print(pandas_series.dtype)
Output :
int64
print(pandas_series.shape)
Output :
(10,)
max(), min(), sum(), median(), mean()… gibi özellikleri Numpy’da olduğu gibi Pandas’ta da kullanabiliyoruz.
print(pandas_series.sum())
Output :
45
print(pandas_series.max())
Output :
9
print(pandas_series.mean())
Output :
4.5
```
### Matematiksel işlemler
```python
print(pandas_series+pandas_series)
Output :
a     0
b     2
c     4
d     6
e     8
f    10
g    12
h    14
i    16
j    18
dtype: int64
print(np.sqrt(pandas_series))
Output :
a    0.000000
b    1.000000
c    1.414214
d    1.732051
e    2.000000
f    2.236068
g    2.449490
h    2.645751
i    2.828427
j    3.000000
dtype: float64
print(pandas_series*pandas_series)
Output :
a     0
b     1
c     4
d     9
e    16
f    25
g    36
h    49
i    64
j    81
dtype: int64
Koşul ifadeleri ile çalışmak
print(pandas_series[pandas_series>pandas_series.median()])
Output :
f    5
g    6
h    7
i    8
j    9
dtype: int64
print(pandas_series[pandas_series == 5])
Output:
f    5
dtype: int64
```
### - DataFrame
DataFrame’leri farklı tipteki sütunlara ve satırlara sahip bir SQL tablosu olarak düşünebiliriz. DataFrame’ler veriyi daha kolay işleyebilmemizi sağlar.

DataFrame’lerin genel kullanımı
```python
my_dataframe = pd.DataFrame(data,index)
```
şeklindedir. Serilerde olduğu gibi DataFrame’lerde farklı türden data parametresi alabilirler. Yukarıdaki kullanımda data parametresi aşağıdakilerden herhangi biri olabilir.

Dictionary’lerden, serilerden veya listelerden oluşan bir dictionary,
2 boyutlu numpy dizisi,
Başka bir DataFrame
```python
#Data dictionary'lerden oluştuğunda
dict1 = dict(a=1, b=2, c=3, d=4)
dict2 = dict(a=5, b=6, c=7, d=8, e=9)
data1 = dict(first=dict1, second=dict2)
df1 = pd.DataFrame(data1)
print(df1)
Output :
   first  second
a    1.0       5
b    2.0       6
c    3.0       7
d    4.0       8
e    NaN       9
#Data serilerden oluştuğunda
s1 = pd.Series([1.1, 2.2, 3.3, 4.4])
s2 = pd.Series(['a', 'b', 'c', 'd', 'e'])
data2 = dict(first=s1, second=s2)
df2 = pd.DataFrame(data2)
print(df2)
Output :
   first second
0    1.1      a
1    2.2      b
2    3.3      c
3    4.4      d
4    NaN      e
#Data başka bir DataFrame'den oluştuğunda
df3 = pd.DataFrame(df2)
print(df3)
```
