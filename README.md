# MAXX6675-raspberry-pi
Tutorial and code on how to setup the Raspberry Pi with a MAXX6675 thermocouple ic board

*Note: This isn't exactly a GitHub-type project, but I wanted to put together a simple guide on using the MAX6675 IC
board with a thermocouple using a Raspberry Pi because I kind of had to piece it together myself. Hopefully at some
point I'll move this to my website instead... but for now, here goes.*

## What you'll need:
* Raspberry Pi running Raspian (I'm using a Rpi 3, but to my knowledge this will work on any version)
* Some way of accessing the Raspbian GUI (I like VNC Viewer but I'm sure there are others)
* MAXX6675 IC Board (like: https://www.amazon.com/gp/product/B00PVTH4MW/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)
* wires
* breadboard
## Install/Update PIGPIO
Good news! Rapspian should come with PIGPIO already installed, so we can just check for OS updates, then running install
will automatically check to see if it is installed and up-to-date. PIGPIO is a library for Rasberry Pi that allows you to control the General Purpose I/O Pins (GPIO) on your Pi.

* open the Raspian terminal and type the following commands:

```bash
sudo apt-get update
sudo apt-get install pigpio python-pigpio python3-pigpio
```
>__Linux Beginner Tip:__ Learning to use the command line can be daunting at first, but here's the breakdown of what you just typed. 
>* __sudo__ is short for __Super User DO__. In short, you're telling the machine that you want to run the command that follows as an administrator.
>   * Sometimes running a command without __sudo__ will give you a permissions error, but you should only use it when necessary.
>* __apt-get__ is the __get__ (or install) command for the __Advanced Packaging Tool__ which is a Linux/Unix package manager. This is a tool that allows you to easily install new software and tools with a single command.
>   * since __apt-get__ is installing new software on your Pi, it requires administrator priveledges, hence the use of __sudo__ with it.
>* __update__ is a command that searches for and installs the latest updates for your Raspbian Operating System
>* __install__ is the command which installs new software from the __apt__ package manager. *Note: Package managers work by installing software for you that a developer has already given them access to. It CAN NOT install software that it doesn't have already have access to. The great thing about __apt__ is that it manages *dependencies* for you, so if you don't have another package that your original download need, __apt__ will install that for you as well.*
>* It's good practice to always run __sudo apt-get update__ before installing new software on your Pi.

*If this worked, then great! Skip the rest of this section and move on to __The MAX6675 Library__. If you got errors,
I'll walk you through manually installing PIGPIO*

Don't fret! There are three other ways to install PIGPIO so try one of them below if apt-get didn't work. __Don't forget that this is to be done from your Raspberry Pi's terminal__

*This method downloads a zipped archive of the source code for PIGPIO from the developer's website, then compiles it on your Pi*
### Method 1
```bash
sudo rm pigpio.zip
sudo rm -rf PIGPIO
sudo wget abyz.co.uk/rpi/pigpio/pigpio.zip
sudo unzip pigpio.zip
sudo make -j4
sudo make install
```

*This method downloads a tar'ed archive of the source code for PIGPIO from the developer's website, then compiles it on your Pi*
### Method2
```bash
sudo rm pigpio.tar
sudo rm -rf PIGPIO
sudo wget abyz.co.uk/rpi/pigpio/pigpio.tar
sudo tar xf pigpio.tar
sudo make -j4
sudo make install
```

*This method downloads the master repository for PIGPIO from the developer's GitHub, then compiles it on your Pi*
### Method 3]
```bash
sudo rm master.zip
sudo rm -rf pigpio-master
sudo wget https://github.com/joan2937/pigpio/archive/master.zip
sudo unzip master.zip
sudo cd pigpio-master
sudo make -j4
sudo make install
```

>__Linux Beginner Tip:__ What do those commands do? 
>* __rm__ is short for __remove__. It is removing the file that follows from your Pi if it already exists to avoid any name conflicts when downloading.
>* __wget__ is short for something like __web get__. It gets content from a website and downloads it to your Pi.
>* __unzip__ is a command that, as its name implies, unzips (decompresses) a .zip file.
>* __tar__ is a command that tar's and untar's a group of files and directories. 
>   * A .tar file is commonly referred to as a tarball. This isn't really compressed like a .zip file unless it's a .targz or .tar.gz file. Instead it is merely a way of grouping files that is commonly used in Linux/Unix environments.
>   * __tar -cvf__ command creates a new .tar
>   * __tar -xvf__ untar's a tarball
>* __cd__ is short for __change directory__. It allows you to navigate through the filesystem of the Pi from the terminal.
>* __make__ is basically a way of running a script that many developers include in their software to automate the compilation and linking of it

## The MAX6675 Library

## Building the Circuit

### The MAX6675 layout
The MAXX6675 should have 5 header pins and two screw terminals.
__Header Pins (to Raspberry Pi)__
SO: Serial Ouput (This will be read by the Pi)
CS: Chip Select (Setting it LOW selects the module)
SCK: Serial Clock (The Pi will supply this)
VCC: 5V supply
GND: Ground

__Screw Terminals (to Thermocouple)__
-(MINUS): Thermocouple minus input
+(PLUS): Thermocouple plus input

*Note: Red should be negative and Yellow should be positive.*

*This isn't always the case though and sometimes the wires will be different colors.
You can always find out which is which by hooking the circuit up and holding the tip
the thermocouple to heat it up. If it's wired correctly, your temperature readings will 
(obviously) go up. If not, they'll go down. If that's the case, switch the + and - and the
issue should be corrected.*

### The Circuit
# IN PROGRESS
