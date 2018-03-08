Github link: https://github.com/Lenonguyen/Acoustic-Sensor.git

-----------------------------------------------
	Acoustic Sensor using RPi3
-----------------------------------------------

Table of Content:

	1. Configuration Instruction
	2. Installation Instruction
	3. List of Project Files
	4. License
	5. Contact Information

1. Configuration Instruction

This section contains 2 parts: hardware configuration and software configuration.

1.1 Hardware configuration

This project is built on a Raspberry Pi 3, with a USB sound card and a microphone.

Ethernet connection is recommended. If an older version of Raspberry Pi is used, certain changes might be necessary.

a. First you have to set USB sound card as default audio device. 

b. Second you need to downgrade the alsa-utils from 1.0.28 to 1.0.25. To do so:

	Use “sudo nano /etc/apt/sources.list” command and add the last line:
	------------------------------------------------------------
	deb http://mirrordirector.raspbian.org/raspbian/ jessie main contrib non-free rpi  
	
	#Uncomment line below then 'apt-get update' to enable 'apt-get source'
	
	#deb-src http://archive.raspbian.org/raspbian/ jessie main contrib non-free rpi
	
	deb http://mirrordirector.raspbian.org/raspbian/ wheezy main contrib non-free rpi
	------------------------------------------------------------
	Run “sudo apt-get update”
	
	Run “sudo aptitude versions alsa-utils” to check if version 1.0.25 of alsa-util is available
	
	Run “sudo apt-get install alsa-utils=1.0.25-4” to downgrade.
	
	Reboot (if necessary).
	
	Run “arecord -r44100 -c1 -f S16_LE -d5 test.wav” to test that your microphone is working. You should see a “test.wav” file in the current folder. 
	
	Put earphone on. Run “aplay test.wav” to check that your recording is okay.

c. Install libcurl library:

	First use command “ls /usr/include/curl” to identify that /usr/include/curl/ folder exists or not.

	If the folder doesn’t exist. Run “sudo apt-get update” to update the application list.

	Run “sudo apt-get install libcurl3” to install the libcurl3.

	Run “sudo apt-get install libcurl4-openssl-dev” to install the development API of libcurl4.

2. Installation Instruction

a. Untar

	After downloading, go to the directory where you keep the file and type the command “tar xvf wave.tar”.

b. Run the program

	Once the file is unarchived, type the command "make" to compile the application.

	After successfully compiled, type "./wave.a" to run the program.

3. List of Project Files

	README.md	: this file

	makefile	: the makefile of this project 

	wave.c		: the module containing functions about wave processing

	wave.h		: the header of wave.c 

	screen.c	: the module containing functions about screen manipulation 

	screen.h	: the header of screen.c 

	comm.c		: the communication module using libcurl 

	comm.h		: the header file of comm.c 

	main.c		: contains main() function 

	raspsound.php	: the server page to receive data 

4. License

Copyright [2017] [Dang Nguyen]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

5. Contact Information

	Dang Nguyen
	Tel: +358 469549954
	Email: lenonguyen@gmail.com
