#Programmatic Wi-Fi
Connect to the wifi using bash scripts. This functionality allows for the user to connect to any Wi-Fi access point in a situation where a a gui normally used to configure Wi-Fi connections is out of reach. Originally developed for the Raspberry Pi.

##Dependencies
If the use is for Raspberry Pi then all dependencies are met. Otherwise, the functioning OS of the user must meet the following:

* Linux (preferably a Debian based disto)
* Pre-downloaded WPA Supplicant. C
..* The script writes to the wpa_supplicant.conf file locatedin `/etc/wpa_supplicant/wpa_supplicant.conf`
##How to download:
Clone this repo and change the directory to the repo itself. Below are the commands to do so:

`$ git clone https://github.com/ev-devs/programmaticWifi.git`

`$ cd programmaticWifi`

##How to use:
The 
