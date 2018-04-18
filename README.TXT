#--------------------------------  Sound Sensor Project  ----------------------------

This project is meant to collect sound level at a proximity of a Raspberry device. This RPi is equipped 
with a USB sound card(C-Media Electronics, Inc. Audio Adapter) and a microphone. The sound is recorded at 16000Hz
sample rate and every second will produce 80 pieces of RMS value as a bar-diagram...

Table of Content:
1. Configuration:
	1.1  Configuring USB Sound Card as Default:
	 - Boot up RPi and apply the sound card. Then, change the default audio devivce to sound card.
	 - Use "lsub" command to check if USB card is mounted.
	 - Run "sudo nano /etc/asound.conf" command and enter the given command:
	  pcm.!default{
	  type plug
	  slave{
	  pcm "hw:1,0"
	        }
	    }
	    ctl.!default{
	    type hw
	    card 1
	 -  Again put this same content under the "command nano .asoundrc".
	 -  Run "alsamixer" to check if the default audio has changed.
	 
	1.2 Install libcurl:
		- Use command "ls/usr/include/curl" to check that curl folder exists or not.
		- If there is no folder, make new by "sudo apt-get update" command.
		- Run "sudo apt-get install libcurl3 to install libcurl.
		- Run "sudo apt-get install libcurl4-openssl-dev" to install development API of libcurl4. 
	 
2. Installation:
	Get the link from https://github.com/dipgau/sound and clone it. After this run "make" command 
	to install it in your device.

3. Operation:
	Run command ./sound.a command to run the application and record the sound.
	
4. Manifest (list of files and short description of their roles)
	 comm.c - This function takes in RMS value of 1 second
	 comm.h - This function is used to access the PHP file located in server and store the recorded data
	 main.c - Record 1 sec of sound into test.wav
	 screen.c - Contains screen manipulation functions, such as clearScreen(), gotoxy(), setColor(), etc 
	 screen.h - This is the header file and contains screen display style and other graphical things 
	 and is accessed by screen.c file
	 sound.a - This file is used to run the application
	 sound.c - The function processes every 200 samples and calculate their RMS value
	 and shows this value as a vertical bar on screen
	 sound.h - This file is used for processing sound (WAV) file
	 makefile - This file updates the changes made in the project

5. Acknowledgements: This project is done under  the guidance of Mr. Gao Chao(original owner of this application) and I would like to thank him very much.
					 
6. License: Permissive FOSS license 
 
7. Contact Information: Dipesh Gautam, e1701299@edu.vamk.fi	
