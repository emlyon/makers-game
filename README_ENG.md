# makers-game

![makers' game](img/makersgame.jpg)


## Material

- 3 plywood boards (1000x600x10mm)
- 1 medium boards (1000x600x3mm)
- 1 PMMA cast sheets (35x400.3mm)
- 1 [Arduino Uno board](https://www.adafruit.com/product/50)
- 1 [prototyping board](https://www.adafruit.com/product/571)
- 1 [Raspberry Pi (Pi 1 Model B)](https://www.adafruit.com/product/1914)
- 1 [USB A/MicroB cable](https://www.adafruit.com/product/592)
- 4 meters of [LED strip](https://www.adafruit.com/product/2562)
- sandpaper
- 30 wood screws (2,5 x 20mm)  
- 2 [10uF capacitors](https://www.adafruit.com/product/2195)
- 10 [10kΩ resistors](https://www.adafruit.com/product/2784)

You will also need:
- 1 laser cutter
- 1 soldering iron
- 1 drilling-screwing machine
- 1 hot glue gun
- 1 tube of wood glue


## Step 1 - Laser cutting

In the "files" tab, **download the documents**.
Then **laser cut** :  

With the **10mm thickness plywood boards**:
- table legs (x4)
- table bottom (x1)
- table top & spare parts (x1)  
Sand the edges to make them clean.


With the **3mm thickness medium**:
-	table outline banner (x4)
-	table grid (x1)  

With the **3mm thickness PMMA**:
- table window (x1)

![laser table top](img/makersgame_dessus.jpg)
![laser table legs](img/makersgame_pieds1.jpg)


## Step 2 - Table assembly

**Table legs assembly**:
- Carefully clean the tapped holes for the screws.
- Screw the plywood boards together with a 90° angle.
- Plug and screw the 4 legs into the table bottom.
*Mind the notches !*  

![Legs 1](img/makersgame_pieds2.jpg)
![Legs 2](img/makersgame_pieds3.jpg)

**Grid assembly**:
- Warning: you will need patience!
- The vertical and horizontal battens need to be pressed together all the way.

**Table outline banner setup**:
- Slot and screw the 6 plywood wedges in the table bottom spots.  
- Once the wedges are fixed, place the 4 curvy pieces that will give rounded angles.
- With a pencil, mark the wedges' middles.
- Place and glue the flexwoods from a wedges' middles (use wood glue).
- Flexwoods' ends must meet: use a little piece of medium in order to keep them together.

![Banner 1](img/makersgame_bordure1.jpg)
![Banner 2](img/makersgame_bordure2.jpg)
![Banner 3](img/makersgame_bordure3.jpg)
![Banner 4](img/makersgame_bordure4.jpg)
![Banner 5](img/makersgame_bordure5.jpg)

## Step 3 - Prepare and setup the LED strip

- We used the LED strip **Adafruit Neopixel** (11 x 19 = 209 leds).
- Cut the LED strip into 19 strips of 11 leds.
- Solder the ends of the mini strips to make something looking like a snake (cf. photo): GND - GND /  DIN - DOUT / 5V - 5V.  
*Careful: the wires lenght needs to be big enough to organise the LED strips just like the picture above.*
- Place the LED strip on the table in such a way that every single LED will be aapproximately in the center of a wooden grid cell.
- Connect your LED strip to Arduino Uno (pin 6)
- Test the LED strip soldering using the Arduino Uno. You can use Arduino example "Simple" from the [« Adafruit Neopixel » library](https://github.com/adafruit/Adafruit_NeoPixel). Every LED should light up.
- Once the soldering is tested, secure the solders using a hot glue gun.
- Plug the grid into the table bottom.
- Upload on the Arduino Uno the program [« arcadeTable_arduino »](https://github.com/emlyon/arcadeTable) available on Github.

![Ruban led 1](img/makersgame_leds1.jpg)
![Ruban led 2](img/makersgame_leds2.jpg)
![Ruban led 3](img/makersgame_leds3.jpg)
![Ruban led 4](img/makersgame_leds4.jpg)


## Step 4 - Program the Raspberry Pi

**Install the Raspberry Pi system**:  
Download and copy the image from [Raspbian Stretch Lite](https://downloads.raspberrypi.org/raspbian_lite_latest) on your Raspberry Pi using [Etcher.io](https://etcher.io/).  
For more details, you can follow the guide: [installing operating system images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).  
Start your Raspberry Pi using a screen, a keyboard and an ethernet cable connected to your internet box.  
*( default id: pi / password: raspberry )*  
Once logged in, you can type: `sudo raspi-config` to configurate the language.  
*( en français: http://www.tropfacile.net/doku.php/raspberry-pi/comment-passer-votre-raspberry-en-francais )*  
Install openFrameworks usign the following guide: [Getting your Raspberry Pi ready for openFrameworks](http://openframeworks.cc/setup/raspberrypi/raspberry-pi-getting-started/)  
Once openFrameworks is installed and tested, you can download the games program and compile it:
```
cd /home/pi/openFrameworks/apps/myApps/
git clone https://github.com/emlyon/arcadeTable.git
make
```
Do not start the program now: you need to connect the Arduino Uno to Raspberry Pi before.
Edit the file `rc.local` in order to launch the game automatically when the Raspberry starts:  
```
sudo nano /etc/rc.local
```
And add the lign `exit`:
```
su pi -c 'cd /home/pi/openFrameworks/apps/myApps/arcadeTable && make run'
```
Click on `Ctrl+x` to quit, then `y` to save.


## Step 5 - Install the arcade buttons

**Prepare the buttons**:
- Solder the electric wires on the buttons' pins:  
10 x 100 cm wires for the 5 buttons of "Player 2"   
10 x 25 cm wires for the 5 buttons of "Player 1"
- Plug anf fix the buttons on the table top board :  
Unscrew the nut.  
Take off one third of the ring by cutting it in 2 different spots.  
Plug the button and tighten the ring from below.

![Boutton 1](img/makersgame_boutons1.jpg)
![Boutton 2](img/makersgame_boutons2.jpg)

**Make the electrical assembly**:
- In this setp, you will need to use a prototyping board.
- Tip: the Arduino Uno, the Raspberry Pi and the power supply will be on « Player 1 » side of the table. Therfore, you will need a bigger wire length for the buttons of « Player 2 ».
- Use male- female cables for the Raspberry Pi pins.
- Use male- male cables for the Arduino Uno pins.

![Fritzing](img/makersgame_fritzing.jpg)  

**Do not forget** to:  
Connect the Arduino Uno to the Raspberry Pi using a USB-USB cable.
Power up the Raspberry Pi using a micro-USB cable: plug the micro-USB side into the Raspberry Pi. Strip the wires on the other cable end and connect them to the capacitors.

How to **connect the 10 buttons to the Raspberry Pi**:  

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

**[Raspberry Pi pinout](http://opensourceforu.com/wp-content/uploads/2017/06/Figure-1-Raspberry-Pi-pinout-diagram.jpg)**  

![Electronic 1](img/makersgame_electronique1.jpg)
![Electronic 2](img/makersgame_electronique2.jpg)

## Step 6 - Finalize the table

- Using a drill, make a 10 mm diameter holl in the table outline banner for the power connector.
- Plug the power connector in the hole.
- Once the electronic and the cables are well organised, use the upperside board to close the table.
- Put the PMMA glass on top of the table grid. It should be maintenained by the table top.

![Perceuse](img/makersgame_perceuse1.jpg)  


#### Vous êtes arrivé à bout, bien joué !

![makers' game rendu](img/makersgame_rendu.png)
