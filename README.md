
#### OpenCV (pour Open Computer Vision) est une bibliothèque graphique libre, initialement développée par Intel, spécialisée dans le traitement d'images en temps réel. 

#### A regarder et à consulter: 
* Computer Vision A-Z Udemy-"Section 1 Face Detection" : https://www.udemy.com/computer-vision-a-z/learn/v4/t/lecture/8254464?start=0
* Introduction to Computer with OpenCV 3 Vision Udemy : https://www.udemy.com/master-computer-vision-with-opencv-in-python/learn/v4/overview
* GitHub de OpenCV pour trouver les haarcascades.xml : https://github.com/opencv/opencv/tree/master/data/haarcascades

#### A retenir : 
```
# Importing the libraries / importer OpenCV 
import cv2 

# Loading the cascades / création de 3 objets de détection
face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml') # face 
eye_cascade = cv2.CascadeClassifier('haarcascade_eye.xml') # eyes 
smile_cascade = cv2.CascadeClassifier('haarcascade_smile.xml') # smile 

# Defining a function that will do the detections / Détection
def detect(gray, frame):
    faces = face_cascade.detectMultiScale(gray, 1.3, 5) 
    # la détection d'effectue sur l'image en noir et blanc
    # 1.3 == coef of image size reduction , 5 == neighbors. 
    
    for (x, y, w, h) in faces:
        cv2.rectangle(frame, (x, y), (x+w, y+h), (255, 0, 0), 2) # tracer un rectangle autour du visage détecté. 
        # (x, y), (x+w, y+h) coordonnées du rectangle ; 
        #couleur du rectangle  (255, 0, 0), épaisseur du rectangle 2.
        
        roi_gray = gray[y:y+h, x:x+w] # zone du visage détectée photo en noir et blanc 
        roi_color = frame[y:y+h, x:x+w] # zone du visage détectée en couleur
        eyes = eye_cascade.detectMultiScale(roi_gray, 1.1, 22)
        # la détection des yeux s'effectue sur la zone du visage en noir et blanc roi_gray.
        for (ex, ey, ew, eh) in eyes:
            cv2.rectangle(roi_color, (ex, ey), (ex+ew, ey+eh), (0, 255, 0), 2) 
            #tracer un rectangle autour de l'oeil détecté.
        smiles = smile_cascade.detectMultiScale(roi_gray, 1.7, 22)
        # la détection du sourire s'effectue sur la zone du visage en noir et blanc roi-gray.
        for (sx, sy, sw, sh) in smiles:
            cv2.rectangle(roi_color, (sx, sy), (sx+sw, sy+sh), (0, 0, 255), 2)
            # tracer un rectangle autour du sourire. 
    return frame # output est l'image en couleur avec les éléments de détection identifiés. 

# Doing some Face Recognition with the webcam
video_capture = cv2.VideoCapture(0) # connexion de la webcam. 
while True:
    _, frame = video_capture.read() #lecture des images de la vidéo
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY) # conversion des images en noir et blanc
    canvas = detect(gray, frame) # la méthode detect prend en input grey et frame et produit comme output canvas
    #l'image en couleur avec les élements de détection identifiés. 
    cv2.imshow('Video', canvas) # générer la vidéo avec les images de canvas. 
    if cv2.waitKey(1) & 0xFF == ord('q'): # cliquer sur q pour fermer la webcam 
        break
video_capture.release()
cv2.destroyAllWindows()
```


