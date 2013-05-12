RaspberryPi
===========

Doing stuff on RaspberryPi

# Auto reconnect wireless network

- option 1: network manager wicd
- option 2: https://raw.github.com/dweeber/WiFi_Check/master/WiFi_Check
- option 3:

(1) create  network-monitor.sh
  #!/bin/bash

while true ; do
   if ifconfig wlan0 | grep -q "inet addr:" ; then
      sleep 60
   else
      echo "Network connection down! Attempting reconnection."
      ifup --force wlan0
      sleep 10
   fi
done

(2) sudo chmod +x ./network-monitor.sh # set executable

(3) sudo ./network-monitor.sh & # run in the background

(4) fg # change to foreground for terminating command using ctrl + c

(5) /etc/rc.local  adding /home/network-monitor.sh & before exit 0 at the end of file # auto connect even rpi reboot

(6) sudo crontab -e; #m h dom mon dow command */5 * * * * /home/pi/network-monitor.sh

reference: http://www.raspberrypi.org/phpBB3/viewtopic.php?f=26&t=16054

# Commands

sudo raspi-config

# Books:

http://shop.oreilly.com/product/0636920023371.do

# Remote Desktop with Pi
Ref: http://www.jeremymorgan.com/tutorials/raspberry-pi/how-to-remote-desktop-raspberry-pi/

On Pi: sudo apt-get install xrdp

Get IP: ifconfig eth0 | grep inet | cut -c21-30

Open Route config page => get IP of Pi

Using mstsc on Window or rdesktop
