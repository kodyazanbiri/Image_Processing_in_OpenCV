# OpenCV İle Gradyanlar
Görüntü gradyanı, bir görüntünün belirli bir noktasında yoğunluk değerlerinin hızla değiştiği bölgeleri ifade eder. Bu gradyan, x ve y yönlerindeki türetilmiş yoğunluk değerlerinden oluşur. Görüntü gradyanı, özellikle kenar tespiti gibi işlemlerde önemlidir.
- Kenar algılamak için OpenCV içerisinde bulunan `“Sobel()”` metotu kullanılır.
```python
dst = cv2.Sobel(src, ddepth, dx, dy, ksize)
```
Parametrelerin açıklamaları:

`src`: Giriş görüntüsü. Bu, gri tonlamalı bir görüntü olmalıdır (bir kanalı olmalıdır).

`ddepth`: Hesaplanan gradyan değerlerinin veri tipini belirtir. Tipik olarak cv2.CV_64F (64-bit float) veya -1 (giriş görüntüsüyle aynı veri tipi) olarak kullanılır

`dx`: X yönündeki gradyan derecesini belirtir. Genellikle 1, 0 veya -1 değerlerini alır.

`dy`: Y yönündeki gradyan derecesini belirtir. Genellikle 1, 0 veya -1 değerlerini alır.

`ksize`: Filtrer boyutunu belirtir. Tipik olarak 1, 3, 5 veya 7 gibi tek sayı değerleri kullanılır.








