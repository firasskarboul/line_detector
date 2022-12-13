# Détection de lignes
__Auteurs :__  
*Laaroussi Fatima Azzahrae*  
*Mohamed Amine Faiz*  
*Karboul Firass*  

# Objectif 
Ce projet est développé dans le contexte de la ROBOCUP. 
La partie qui nous a été confiée consiste à détecter les lignes du terrain de football. Donc pour
une image donnée en entrée de notre programme, on doit pouvoir obtenir une image en sortie
dont uniquement les lignes sont représentées sous forme de masque.

# Approche de résolution 
Nous avons exploré en amont de la résolution plusieurs méthodes, notamment une approche par
Deep Learning, mais qui nous a été déconseillé par nos encadrants à cause de notre faible base
de données, en effet, ne disposant pas assez d’images de lignes pour entraîner notre réseau de neurones,
nous ne pouvons pas nous aventurer dans cette piste pour la détection de lignes d'un terrain qui est en
soit une reconnaissance complexe.

Nous nous sommes alors penchés vers des méthodes de traitement d’images vu en cours d'images telles que la méthode d'érosion/dilatation, méthode du filtrage par médiane, et la méthode de recours aux informations données par l'histogramme d'une image.

# Méthode de l'Histogramme
Les étapes suivies pour ce filtrage sont les suivantes :  
 - appliquer un filtre de __Canny__ à l'image dont on veut détecter la ligne  
   
   
 ![im](https://github.com/firasskarboul/line_detector/blob/main/readme/image.png?raw=true)
  
 - générer une fonction qui affiche l'histogramme de cette image en RGB grace à la librairie skimage  
 - analyser l'histogramme de fréquence pour ne garder que les nuances dominantes de l'image ( qui correpondent au terrain)
 - créer un masque qui ne garde que les nuances dominantes(noir) et supprime toutes les autres(blanc)  
   
     ![im1](https://github.com/firasskarboul/line_detector/blob/main/readme/image1.png?raw=true)
  
     
 - appliquer un filtre médian de la librairie OpenCV pour lisser l'image et ainsi la nettoyer des "résidus" potentiellement non détectés par notre 
 filtrage en fréquences  
   
   ![im2](https://github.com/firasskarboul/line_detector/blob/main/readme/image2.png?raw=true)
     
     
 - dilater l'image puis l'eroder
 - la dilater encore une fois puis l'éroder
 - lui appliquer finalement un filtre médian pour ne garder que la ligne qui nous interesse
  
  
  ![im4](https://github.com/firasskarboul/line_detector/blob/main/readme/image4.png?raw=true)


# Installation des dépendances 
Pour installer tous les packages utilisés dans ce projet, veuillez utiliser la commande :  
$ pip install -r requirements.txt

