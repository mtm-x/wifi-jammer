# wifi-jammer
wifi jammer using aircrack-ng. 
# What is deauth attack
A deauth attack sends forged deauthentication packets from your machine to a client connected to the network you are trying to jam. These packets include fake "sender" addresses that make them appear to the client as if they were sent from the access point themselves. Upon receipt of such packets, most clients disconnect from the network and immediately reconnect.
# Getting started 
Install [aircrack-ng](https://github.com/aircrack-ng/aircrack-ng) on your machine and make sure your wifi card supports monitor mode 
# Jamming
### Monitor Mode
1. type `iwconfig` in your terminal

   ![1](https://github.com/mtm-x/wifi-jammer/assets/88881685/8e6b01cb-34cc-4fad-babe-42c7d38db355)

In this instance, my wireless card is called wlan0.

2. Now run 

```
airmon-ng start wlan0
```
where wlan0 is your network card. This will put your card into monitor mode which allows the card to monitor all traffic on the network.




