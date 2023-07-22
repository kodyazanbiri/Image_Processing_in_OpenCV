# Proje1 - El Takibi(Hand Tracking)
OpenCV ve MediaPipe kütüphanelerini kullanarak bir web kamerasından gerçek zamanlı görüntü akışını yakalayan ve MediaPipe ile yüz ve el izleme gibi nesne algılama işlemlerini gerçekleştiren örnek bir program.
```python
import cv2
import time
import mediapipe as mp

cap = cv2.VideoCapture(0)

mpHand = mp.solutions.hands

hands = mpHand.Hands()

mpDraw = mp.solutions.drawing_utils

pTime = 0
cTime = 0

while True:
    success, img = cap.read()
    imgRGB = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    
    results = hands.process(imgRGB)
    print(results.multi_hand_landmarks)
    
    if results.multi_hand_landmarks:
        for handLms in results.multi_hand_landmarks:
            mpDraw.draw_landmarks(img, handLms, mpHand.HAND_CONNECTIONS)
            
            for id, lm in enumerate(handLms.landmark):
                # print(id, lm)
                h, w, c = img.shape
                
                cx, cy = int(lm.x*w), int(lm.y*h) 
                
                # bilek
                if id == 4:
                    cv2.circle(img, (cx,cy), 9, (255,0,0), cv2.FILLED)
    
    # fps
    cTime = time.time()
    fps = 1 / (cTime- pTime)
    pTime = cTime
    
    cv2.putText(img, "FPS: "+str(int(fps)), (10,75), cv2.FONT_HERSHEY_PLAIN, 3, (255,0,0), 5)
    
    cv2.imshow("img", img)
    cv2.waitKey(1)
```
- Gerekli kütüphaneler ve modüller (cv2, time, mediapipe) içe aktarılır. Ardından, `cv2.VideoCapture(0)` komutu, sisteminizdeki ilk web kamerasını (ID 0) kullanarak bir VideoCapture nesnesi oluşturur. Bu nesne, web kameradan gelen görüntü akışını yakalamak için kullanılır.
- Sonrasında, `while True:` döngüsü içinde, sürekli olarak web kamerasından görüntü alınır ve işlenir. Bu döngü, program kullanıcısı tarafından elle sonlandırılana kadar devam eder.
- Döngü içindeki `cap.read()` işlevi, web kameradan bir görüntü çerçevesi yakalar. Fonksiyon, iki değer döndürür: success ve `img. success` değişkeni, çerçevenin başarıyla okunup okunmadığını gösterir (True veya False değeri alır). img değişkeni, yakalanan görüntü çerçevesini temsil eden bir numpy dizisidir.     
- `mpHand = mp.solutions.hands` Bu satırda, mp.solutions.hands modülünü mpHand adı altında bir değişkene atıyoruz. Bu adımla, el izleme işlemleri için gerekli olan sınıf ve işlevleri içeren mpHand değişkeni oluşturulur.     
- `hands = mpHand.Hands()` Bu satırda, mpHand değişkeninde oluşturduğumuz sınıfı çağırarak el izleme için bir nesne oluşturuyoruz. mpHand.Hands() ifadesi, el izleme işlemlerini gerçekleştirmek için kullanılacak bir Hands sınıfı örneğini oluşturur. Böylece hands adlı değişken, el izleme işlemleri için gerekli olan sınıfın bir örneğini tutar.   
    
    
    
