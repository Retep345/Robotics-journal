# Journal Peter Allen ROCO 222
          (partnered with Will Redhead)
          
## Markdown
markdown is a text editing syntax that simplifies HTML coding for ease of use and speed.

* Headings are done with \# with 1 used for the main header and increasing ammounts for subsiquent headers to denote importance /(two for a secondary header, 3 for tertiary, so on)

* using a \\ leaves the symbol unedited for visual or literal use.

* *italics* and **bold** use \*'s either end, 1 for italics and two for bold

* bulletpoints use a single \* at the start

* number lists use \1. or any number to organise like a bullet point list

>block
>quotes use the \> at the start

* using 3 \' change the text into a code format, such as javascript

'''javascript
function test()
'''

* -[x] a tick box is done with an x between square brackets
  -[ ] an unticked box is done without the x

* an image can be attached from a url using a \! before a given name in a square bracket and a url or link in a curved bracket such as \!\[image name](/images/website .com/image.png)




## Command Lines

using the terminal of a linux-based system, we can enter code to interact with dirrectories

* known commands:
    -$ ls                             lists sub-directories within current directory
    
    -$ cd (subdirectory)              enter named subdirectory
    
    -$ mkdir (name)                   creates a directory within current location with the netered name
    
    -$ echo "hello"                   the terminal responds 'Hello'
    
    -$ cat hello.md                   terminal responds 'Hello' while creating a formal document called hello.md
    
    -$ cp hello.md hello-again.md     copies information over
    
    -$ rm hello.md                    removes hello.md
    
    -$ rm - rf                        remove (recursive forced)   removes file within permission limitations
    
    -$sudo rm - rf                    removes with sudo permissions (very dangerous if used incorrectly)
    
    -$ cat/proc/cpuinfo               displays information about the computer from CPU
    
    -$ man (command)                  gives help information about the command, with man being short for manual.


## DC Electric Motor
using copper loops and magnets, we plan to create an electric motor.

### building a basic motor
1. put nail into either flat end of a cork core

2. apply 2 strips of copper tape at one end with a gap between. these act as a **commutator**

3. wrap copper wire lengthways around the core between the commutator plates

4. sand the ends of the wire and solder onto plates

5. using large paperclips, create a rack to hold the nails to act as an axis of rotation

6. face magnets so that they attract, but spaced away from eachother either rounded side of the central rotor

7. apply current using wires touching commutator

![motor](https://user-images.githubusercontent.com/32262003/34777911-b20a477c-f613-11e7-9549-e796ee3bfa0b.jpg)

* the motor operates by applying current to the commutator plates, transfering current through the loops and generating a magnetic field. the strong magnets interact with that field, pulling or pushing it and forcing it to turn so it can reach equilibrium. by having the source of current unattached to the commutator, the brushes switch which plate they contact, therefore inverting the magnetic field. the momentum carrier it over and it then rotates to reach its new equilibrium, repeating as long as there is current switching between the commutator plates.

![motor spin](https://user-images.githubusercontent.com/32262003/34778485-5ee793cc-f615-11e7-9779-73bbb3c2bf28.gif)

* to improve the motor, a second coil can be added. this increased rate of alternation makes it less likely for the motor to stall and can also provide more power behind it. adding a second coil doubles the commutators, which can be extended to close up the space made by the coils to keep more contact on the motor during rotation. the above gif has two coils on the core


### Encoder
using an infared LED and a LDR, the rate of the motor can be relatively measured.

attaching a card disc with a segment removed, the LDR will read infared light once per rotating, and trigger a signal that will be sent to an arduino board. the board will then count each "pulse" and add to a count, printing to a screen. during tha practical, me and my partner timed 20 seconds and multiplied the count by 3 to get an RPM for the motor. after 3 readings we got an average of roughly 11,000 RPM.

the code below is what the arduino board was programmed with:

>/#define NOT_AN_INTERRUPT -1
>
>const byte ledPin = 13;
>const byte interruptPin = 2;
>volatile byte state = LOW;
>int pulseCounter = 0;

>void setup() {
> pinMode(ledPin, OUTPUT);
> pinMode(interruptPin, INPUT);
> Serial.begin(9600); // set up Serial library at 9600 bps

>// configure the interrupt call-back: blink is called everytime the pin
>// goes from low to high.
> attachInterrupt(digitalPinToInterrupt(interruptPin), blink, RISING);
>}

>void loop() {
> digitalWrite(ledPin, state);
> String counterString = String(pulseCounter);
> Serial.println(counterString); // prints hello with ending line break
> delay(1000); // wait 1s
>}

>void blink() {
> state = !state;
> pulseCounter++;
>}




## Motors

### Stepper Motors



the code used for one-phase movement:
**void setup(){
 
 **//set up channels A and B
 pinMode(12, OUTPUT);  //Initiates Motor Channel A pin
 pinMode(9, OUTPUT);   //Initiates Brake Channel A pin
 pinMode(13, OUTPUT);  //Initiates Motor Channel B pin
 pinMode(8, OUTPUT);   //Initiates Brake Channel B pin
}

**void loop(){
  
  **digitalWrite(12, HIGH); //Establishes forward direction of Channel A
  digitalWrite(9, LOW);   //Disengage the Brake for Channel A
  analogWrite(3, 255);    //Spins the motor on Channel A at full speed
  digitalWrite(13, HIGH); //Establishes forward direction of Channel B
  digitalWrite(8, LOW);   //Disengage the Brake for Channel B
  analogWrite(11, 0);    //Spins the motor on Channel B at full speed
  
  **delay(1);
  
  **analogWrite(3, 0);    //Spins the motor on Channel A at full speed
  **analogWrite(11, 255);    //Spins the motor on Channel B at full speed

  **delay(1);
  
  **digitalWrite(12, LOW); //Establishes backward direction of Channel A
  analogWrite(3, 255);    //Spins the motor on Channel A at full speed
  digitalWrite(13, LOW); //Establishes backward direction of Channel B
  analogWrite(11, 0);    //Spins the motor on Channel B at full speed
  
  **delay(1);
  
  **analogWrite(3, 0);    //Spins the motor on Channel A at full speed
  analogWrite(11, 255);    //Spins the motor on Channel B at full speed

  **delay(1);
}

### Servo Motors

the servo motors are controlled by changing the length of time the servo's pin is HIGH. by adding values from exernal potentiometers to a constant we could move the servo motor in a 180 degree range. setting a second pin with a second servo motor and potentiometer meant we could control the two independently.
as the last part of the practical module, we we're required to create a 3D model that will then be 3d-printed with plastic and controled using the 2 servo motors provided.


### Robot Arm
with only 2 servo motors, that means that for the robot to be an "arm" it requires one servo to be a hand that can open and close while the other needs to move that hand from one location to another, thus giving the arm a range it can reach within.

with only servo motors, the hand became a claw with two digits, one immovable, while the other could open and close to grab objects.
the arm was more complex, as it needed horizontal motion. this was achieved by having the servo move a "bicep", which had a "forearm" hinged on it. the end of the forearm would then hinge on a hole in a rail that went across solid points, keeping it level, meaning that if the servo turned 'X' degrees, the "elbow" would move '2X' degrees and so the wrist would hinge 'X' degrees, keeping the hand level and moving forward and back, while the elbow rises and falls with movement.












