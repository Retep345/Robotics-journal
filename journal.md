# Journal Peter Allen ROCO 222

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

* a url can be attached using a \! before a given name in a square bracket and a url in a curved bracket ![example](https://dle.plymouth.ac.uk/) using the DLE site


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


## Electric Motor
using copper loops and magnets, we plan to create an electric motor.

### building a basic motor
1. put nail into either flat end of a cork core

2. apply 2 strips of copper tape at one end with a gap between. these act as a **commutator**

3. wrap copper wire lengthways around the core between the commutator plates

4. sand the ends of the wire and solder onto plates

5. using large paperclips, create a rack to hold the nails to act as an axis of rotation

6. face magnets so that they attract, but spaced away from eachother either rounded side of the central rotor

7. apply current using wires touching commutator

* the motor operates by applying current to the commutator plates, transfering current through the loops and generating a magnetic field. the strong magnets interact with that field, pulling or pushing it and forcing it to turn so it can reach equilibrium. by having the source of current unattached to the commutator, the brushes switch which plate they contact, therefore inverting the magnetic field. the momentum carrier it over and it then rotates to reach its new equilibrium, repeating as long as there is current switching between the commutator plates.

* to improve the motor, a second coil can be added. this increased rate of alternation makes it less likely for the motor to stall and can also provide more power behind it. adding a second coil doubles the commutators, which can be extended to close up the space made by the coils to keep more contact on the motor during rotation.










