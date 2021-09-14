# Using the Raspberry Pi with Touchscreen and Soundcard
Tested with Raspberry Pi 3 Model B Plus Rev 1.3, IQaudIO Pi-DAC+ Soundcard and 7" touchscreen display:

1) Burn Raspian image to SD card
2) Enable ssh by creating an empty file on the SD card via: `touch /boot/ssh` 
3) Add network info by creating a new file `wpa_supplicant.conf` and insert the following lines:

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```

5) Adjust the following file: `/boot/config.txt`
    1) Comment this line out: `#dtparam=audio=on`
    2) Add this line to the end of the file: `dtoverlay=iqaudio-dacplus`
    3) Uncomment this line: `hdmi_drive=2`

4) Insert SD card into Raspberry Pi and boot -> Wait until installation has finished

Both the display and the audio from the soundcard should work now.



# Sources: 
* https://desertbot.io/blog/headless-raspberry-pi-3-bplus-ssh-wifi-setup
* https://raspberrypi.stackexchange.com/questions/44/why-is-my-audio-sound-output-not-working
* https://datasheets.raspberrypi.org/iqaudio/iqaudio-product-brief.pdf
