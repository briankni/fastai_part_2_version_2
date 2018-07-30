Paperspace Environment Setup
======

This file contains my notes on how to set up headless access for a Fast.AI course paperspace instance with Visual Studio Code.  
The advantages of doing the set up this was over following the cource recommendation to make a local installation are:
  1) The Jupyter notebooks and the code editor are using the same source files.
  2) Visual studio code is now accessible from anywhere that paperspace can be used.
  
## Local Setup
I'm using OS X 10.11.4.  Local setup is easy. On top of this install:
  1. Chicked Of the VNC.  I have 2.0b4 

Add some lines to the .bash_profile:

#Quick paperspace access  
alias paperspace ssh -L 5900:localhost:5900 paperspace@184.105.86.194 launchFast  
AI



##Remote Setup
Fast.AI is based on Ubuntu 16.04.  Install the following packages (and any dependencies):
1. sudo apt-get install x11vnc
2. sudo apt-get install xvfb
3. sudo apt-get install xfce4
4. sudo apt-get install ubuntu-desktop
5. Follow directions to install VS Code: https://code.visualstudio.com/docs/setup/linux

Next, configure xfce4 into the user.xinitrc so that it is started with X-Windows:
x11vnc &
exec startxfce4


Change the X11 server to Xvfb by editing /etc/X11/xinit/xserverrc
#!/bin/sh

exec /usr/bin/Xvfb -nolisten tcp -screen 0 1280x1024x24 "$@"



~                                                                               
~                                      
