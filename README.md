#Programmatic Wi-Fi
Connect to the wifi using bash scripts. This functionality allows for the user to connect to any Wi-Fi access point in a situation where a a gui normally used to configure Wi-Fi connections is out of reach. Originally developed for the Raspberry Pi.

##Dependencies
If the use is for Raspberry Pi then all dependencies are met. Otherwise, the functioning OS of the user must meet the following:

1. Unix based OS (preferably Linux, and even better if it is a Debian based distro)
2. Pre-downloaded WPA Supplicant client.
    * The `wifi_con.sh` script writes to the wpa_supplicant.conf file locatedin `/etc/wpa_supplicant/wpa_supplicant.conf`, thus the user NEEDS this file already within.


##How to download:
Clone this repo and change the directory to the repo itself. Below are the commands to do so:

`$ git clone https://github.com/ev-devs/programmaticWifi.git`

`$ cd programmaticWifi`

##How to run:
The scripts invoke commands only priveleged users are allowed to run as they access sensitive files on the system. Thus, in order to run the scripts run them with sudo priveleges as such:

`$ sudo ./wifi_script.sh`

`$ sudo ./wifi_con.sh`

`$ sudo ./wifi_con.sh`

##Fine details (what does it actually do???)
Great question actually. As stated before, these three scripts are used to provide details and configure the network connections around you. Below are the details and functionality of each. Keep in mind the
following acronyms on our journey through the world of wireless and wired networks

wlan0 = Wireless Local Area Network Interface one: in simple terms, when referring to wlan0 think Wi-Fi

eth0 = Ethernet Interface one: in simple terms, when referring to eth0 think ethernet

###wifi_script.sh

#####wlan0
Relating to Wi-Fi the script provide information about wireless local area network connections. Assuming there are Wi-Fi access points available, said access points will be listed, providing the quality
of the signal and the signal level in db. The higher the quality and signal level the better the connection so be SURE to choose the one with the best connection(for the inquisitive mind, refer to the man pages for [iwconfig](http://linux.die.net/man/8/iwconfig) (A main tool in the script itself) for details on signal link quality).
The script also reveals whether or not the networks in an area require a passkey. And finally, the names of each connection are also displayed next to the term "ESSID".

#####eth0
Relating to ethernet, the script will only tell whether or not a link to eth0 is established, meaning it will tell the user if an ethernet connection is available.

#####Summary (TL;DR for the lazies)
Displays Wi-Fi names and signal strengths. If an ethernet is connected it will tell the user.

#####Example run
```
$ sudo ./wifi_script.sh
Ethernet registered on eth0

Wi-Fi access points registered on wlan0

Quality:67/70 Signal-level:-43 dBm Encryption key:off ESSID:"EVGuests" 
Quality:68/70 Signal-level:-42 dBm Encryption key:on ESSID:"EVEmployees" 
Quality:68/70 Signal-level:-42 dBm Encryption key:on ESSID:"EVBosses" 
```
###wifi_con.sh
#####wlan0
Relating to Wi-Fi, the script prompts the user to enter an access point as displayed from the previous script. When done entering the Wi-Fi name, the user should enter the correct password, assuming one is needed. When the correct
password is entered then given a few seconds, the Wi-Fi network card will be reset and then connected to the chosen network

#####eth0
Relating to ethernet, this script tells the user that ethernet is used by default and gives them the option to switch between ethernet and Wi-Fi IF they want to.

#####Summary (TL;DR for the lazies)
Connects the user to the specified access point.

#####Example run
```
$ sudo ./wifi_con.sh
Access point: EVBosses
Passkey:
Is this correct (y/n): wedembosse$
y
```

###wifi_cur.sh 
#####wlan0
Relating to Wi-Fi, this script just displays the current connection.
#####eth0
Tell if connected to ethernet.
#####Example run

```
$ sudo ./wifi_cur.sh
Current Wi-Fi connection: "EVBosses"
```
##Bugs and pitfalls (make note of these)
* For the wifi_con.sh I have not tested the flipping between Ethernet and Wi-Fi on the Raspberry Pi. Will do so when I have access to the Raspberry Pi

* Though the script is built to filter out duplicates it is not built to filter out duplicate routers. IF there are multiple routers with the same ESSID in one area it will list them all with their respective strengths. 
Currently working on a fix.

* Recovering ethernet connection after switching from ethernet to Wi-Fi via the wifi_con.sh is not yet configured. To do so would require running "ifconfig eth0 up" which is not in any of the scripts yet.

* At times, displaying the access points over the wlan0 is slower than other times. 

* Displaying the difference in strength between Wi-Fi and ethernet strength is not yet configured.

