# makers-game

![Mountain View](img/makersgame.jpg)

## Step 1 - Découper les pièces

Dans l’onglet fichiers, <b>télécharger les documents</b>.
Et **découper à la laser** :

En contre-plaqué de 10mm d’épaisseur:

- pieds de la table (x4)
- plateau du dessous (x1)
- plateau du dessus avec pièces annexes (x1)  
Poncer les rebords des découpes afin d’obtenir un rendu propre.


En médium de 3mm d’épaisseur:
-	4 x bandeaux contours de la table (médium)
-	1 x quadrillage intérieur (x1)


## Step 2 - Assembler la table

Assembler les pieds:
- Nettoyer soigneusement les trous taraudés des vis.
- Visser les planches de bois deux à deux avec des vis à bois (2,5 x 20mm)
- Insérer les 4 pieds dans le plateau du dessous et visser
  Attention à ne pas abimer les encoches !

Assembler la grille:
- Vous munir de patience !
- Les lattes verticales et horizontales doivent être bien totalement enfoncées les unes dans les autres.

Mettre en place le bandeau:
- Trouver le milieu de la largeur et notez-le sur la cale en bois.
- Placer le flexwood à partir du milieu de la cale en bois
- Coller le flexwood (mettre de la colle à bois sur les parties ou il y a les cales).
- Pour rejoindre les 2 bouts de flexwood : collez un petit bout de medium 3mm permettant de les réunir et de solidifier l’ensemble.


## Step 3 - Préparer et installer le ruban de LED

- Nous avons utilisé le ruban de leds Adafruit Neopixel (11 x 19 = 209 leds).
- Couper votre ruban en 19 rubans de 11 leds.
- Souder les extrémités de vos rubans de façon à réaliser un « serpent » (cf. photo): GND - GND /  DIN - DOUT / 5V - 5V. Attention: la longueur de vos fils doit être suffisante pour pouvoir disposer les leds comme sur la photo.
- Une fois les soudures réalisées, les fixer avec un point de pistolet à colle.
- Placer le ruban LED sur la table. Faire en sorte que chaque LED soit à peu près au milieu de chaque case de la grille. Les câbles doivent pouvoir passer entre les encoches supérieures des pieds.
- Connecter votre ruban de led à l'Arduino Uno (pin 6)
- Tester les soudures de votre ruban à l’aide de l’Arduino Uno. Pour cela, nous utilisons l’exemple « Simple » de la <a href="https://github.com/adafruit/Adafruit_NeoPixel">librairie « Adafruit Neopixel »</a>. Vérifier que touts vos led s'allument correctement.
- Une fois testé, disposer parfaitement votre ruban de legs et enfoncer la grille dans le plateau du dessous de la table.
- Téléverser le programme disponible sur Github: « arcadeTable_arduino » // https://github.com/emlyon/arcadeTable

// IMAGE BRANCHEMENT LED//


## Step 4 - Programmer la Raspberry Pi

Télécharger et copier l’image de [Raspbian Stretch Lite](https://downloads.raspberrypi.org/raspbian_lite_latest) sur votre Raspberry Pi en utilisant [Etcher.io](https://etcher.io/).  
Vous pouvez suivre le guide [installing operating system images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour plus de détails.  
Démarrez votre Raspberry Pi avec un clavier, un câble ethernet relié à votre box internet et un écran branchés.  
( identifiant par défaut: pi / mot de passe: raspberry )  
Une fois identifié, vous pouvez taper: `sudo raspi-config` pour configurer la langue du clavier ( en français: http://www.tropfacile.net/doku.php/raspberry-pi/comment-passer-votre-raspberry-en-francais )  
Installez openFrameworks en suivant le guide suivant: [Getting your Raspberry Pi ready for openFrameworks](http://openframeworks.cc/setup/raspberrypi/raspberry-pi-getting-started/)  
Une fois openFrameworks installé et testé, vous pouvez maintenant télécharger le code des jeux et le compiler:
```
cd /home/pi/openFrameworks/apps/myApps/
git clone https://github.com/emlyon/arcadeTable.git
make
```
Ne lancez pas le programme maintenant: si l'arduino n'est pas branchée, le programme ne peut pas fonctionner.  
Pour que le jeu se lance automatiquement au démarrage, éditez le fichier `rc.local`:  
```
sudo nano /etc/rc.local
```
Et ajouter avant la ligne `exit`:
```
su pi -c 'cd /home/pi/openFrameworks/apps/myApps/arcadeTable && make run'
```
Faites `Ctrl+x` pour quitter, puis `y` pour sauvegarder.


## Step 5 - Installer les boutons d’arcade

// AJOUTER SCHEMA FRITZING //
- Utiliser une plaque de prototype pour réaliser vos soudures.
- Attention: l’Arduino Uno, la Raspberry Pi et l’alimentation seront du côté du « Player 1 ». Il faut donc une certaine longueur de fil pour les boutons d’arcade du « Player 2 ».
- Utiliser des cables male - femelle pour les pins destinées à être connectées au Raspberry Pi.


Voici les branchements de boutton sur la Raspberry Pi:
Player 1 - UP button: pin 23  
Player 1 - DOWN button: pin 24  
Player 1 - LEFT button: pin 10  
Player 1 - RIGHT button: pin 9  
Player 1 - RESET button: pin 11  
Player 2 - UP button: pin 4  
Player 2 - DOWN button: pin 17  
Player 2 - LEFT button: pin 18  
Player 2 - RIGHT button: pin 27  
Player 2 - RESET button: pin 22

 // IMAGE PINOUT//


## Step 6 - Finaliser la table

- A l’aide d’une perceuse réaliser un trou de 10mm de diamètre au niveau de l’alimentation dans le bandeaux de contour de la table.
- Y insérer le connecteur pour l’alimentation 5V.
