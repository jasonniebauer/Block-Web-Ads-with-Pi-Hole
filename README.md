# Deploy Network-wide Ad Blocking

Pi-Hole is an open source ad blocker.

Note: Headless vs using a monitor (gui)

## Outline of Basic Steps
Format micro SD card (4GB)
Write image to micro SD card (Stretch Lite, no GUI)

**SSH Quickstart**
- Enable SSH: Add a `ssh` file without an extension to the micro SD card before powering Raspberry Pi on
- Boot up Raspberry Pi
- Scan local network to identify IP address
- SSH pi@IPADDRESS

## Login
Login to the Raspberry Pi using the following default credentials:  
username: pi  
password: raspberry

### Change Password
Change user password, because we will be enabling remote access to our Raspberry Pi. If someone was to gain access to your network and find the IP address of your Raspberry Pi it would be really easy for them to get in by using the default login credentials.

passwd *username*
```shell
passwd pi
```

## Enable Remote Access
To enable SSH, enter the command below to open Raspberry Pi's configuration graphical user interface.
```shell
sudo raspi-config
```
Using the arrow keys select option 5 for **Interfacing Options** and press <kbd>Enter</kbd>

Now select the P2 option for SSH and hit <kbd>Enter</kbd>

You will be asked if you would like the SSH server to be enabled. Select **Yes** and press <kbd>Enter</kbd>

Exit out of the configuration graphical user interface by using the right arrow key to select **Finish** and press <kbd>Enter</kbd>

## Get the Raspberry Pi's IP Address

```shell
ifconfig
```

Under ethernet 0 we can see our *inet* address which is going to be the IP Address of the Raspberry Pi.

## Install Pi-Hole

```shell
curl -sSL https://install.pi-hole.net | bash
```
Hit <kbd>Enter</kbd> a bunch...

## Select Upstream DNS Provider
Select OpenDNS, or custom

## Set Static IP Address
This will differ depending on your network. In our case, we're going to leave as is and select **Yes** and press <kbd>Enter</kbd>

## Installation Complete
We now have our IP address url and password that we need to login to the web interface.

---

[Adafruit PDF for Pi-Hole Zero](https://cdn-learn.adafruit.com/downloads/pdf/pi-hole-ad-blocker-with-pi-zero-w.pdf)  
[Setting up a Pi Hole for whole-home ad/tracker blocking](https://www.jeffgeerling.com/blog/2017/setting-pi-hole-whole-home-adtracker-blocking)
[BalenaEtcher](https://www.balena.io/blog/deploy-network-wide-ad-blocking-with-pi-hole-and-a-raspberry-pi/?utm_source=efp&utm_medium=etcher&utm_campaign=balena-pihole&utm_content=v1&u_id=16ba5f0d4e03a6-0efcab481e1106-76766f30-130980-16ba5f0d4e190e)
[DanTheIOTMan.com](https://dantheiotman.com/2018/10/23/blocking-web-ads-with-pi-hole/)
