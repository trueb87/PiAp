# PiAp
Script to help someone turn their pi into an AP. The raspberry pi must be connected via ethernet.

1. Write the Raspbian Lite image to an SD card using a program like etcher.
2. After writing the image to the SD card create a empty file called "ssh" in /boot while it is mounted to the computer.
    1. You will need to remove and insert the card agai
3. Place the SD card into the raspberry pi and boot it up, obtain the IP address
    1. The IP address can be found by using nmap to scan the network. On your local computer install nmap and run `sudo nmap -sS -p 22 192.168.1.1/24` You may need to change the ip address range
     to match your network. This will list all the devices on the network that have running SSH connections. Look for the
     device that indicate they are a raspberry pi.
4. (optional) To make sshing into your pi easier, use your ssh key `ssh-copy-id pi@<piaddress>`. 
Enter in your password ("raspberry" by default) and then you will no longer need to type in your raspberry pi's password
again from your computer.
5. SCP the whole WARP directory into the raspberry pi. The credentials by default will be pi / raspberry
6. SSH into your Raspberry Pi
7. Change the password on your raspberry pi even if you added your SSH key to the pi. Use `passwd` to change the password
8. Set your wifi region
    1. Run `sudo raspi-config`
    2. Select `Localisation Options` (number 4)
    3. Select `Change Wi-Fi Country` (I4)
    4. Select `United States`
    5. Hit enter twice, then esc once
9. Run `sudo ./wifiConfig.sh`, this will configure the raspberry pi to act as a wifi access point
    1. The shell script may not have execution privileges, if it does not use chmod to make it executable 
    `chmod 755 wifiConfig`
10. Once script has finished executing type in `exit` and then power cycle the raspberry pi
