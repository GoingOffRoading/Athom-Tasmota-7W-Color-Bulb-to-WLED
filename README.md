# Athom-Tasmota-7W-Color-Bulb-to-WLED

![Athom-Tasmota-7W-Color-Bulb](https://github.com/GoingOffRoading/Athom-Tasmota-7W-Color-Bulb-to-WLED/blob/main/athom7wbulb.png "Athom-Tasmota-7W-Color-Bulb")

If you've purchased one of these 7w PWM RGBW bulb with the Tasmota firmware from the [Athom.tech](https://www.athom.tech/blank-1/color-bulb) store or Aliexpress, and desire to convert the bulb to WLED firmware, here are the required steps and files.

## WARNING

**Proceed at your own risk.**  These steps worked for me, and [has worked for others](https://www.reddit.com/r/WLED/comments/pvtuvx/comment/hf6mc4t/?utm_source=share&utm_medium=web2x&context=3), but that does not guaruntee that they will work for you.  There may be additional steps, firmware, or etc that you must take.  You may brick your device, and require refashing using GPIO pins or replacing the device.  Please thoughoughly research convering ESP8266 firmware before proceeding.

## Steps

1. Download [tasmota-minimal.bin.gz](https://github.com/GoingOffRoading/Athom-Tasmota-7W-Color-Bulb-to-WLED/blob/main/tasmota-minimal.bin.gz) and [WLED_0.14.0_ESP8266.bin.gz](https://github.com/GoingOffRoading/Athom-Tasmota-7W-Color-Bulb-to-WLED/blob/main/WLED_0.14.0_ESP8266.bin.gz) from this repo, or from WLED/Tasmota directly.
2. Log into the Tasmota UI.
3. Click into the console, and enter: "SetOption78 1".
4. Return to the main menu, click on 'Firmware Upgrade'. In the bottom "Upgrade by file upload" section, choose the "WLED_0.14.0_ESP8266.bin.gz" file from step 1.  Click 'Start Upgrade'.
5. Skip steps 6 & 7 if you did not recieve any errors.

If you recieved an error about free space: Some of these (and similar) bulbs are manufactured with reduced flash space.  I believe my bulbs shipped with the ESP8285 which only have 2M of flash (instead of the usual 4M that ESP8266 carry).  My ESP8285 was shy of having enough free space to upgrade the firmware by a dozen KBs.  If this is your scenario, follow these additional steps.   

6. Return to the main menu, click on 'Firmware Upgrade'. In the bottom "Upgrade by file upload" section, choose the "tasmota-minimal.bin.gz" file from step 1.  Click 'Start Upgrade'.  This installs the smallest possible binary of Tasmota, which should free up sufficient space on the ESP8285/8266 for the install.
7. When that is complete, click on 'Firmware Upgrade'. In the bottom "Upgrade by file upload" section, choose the "WLED_0.14.0_ESP8266.bin.gz" file from step 1.  Click 'Start Upgrade'.

8. Log into the WLED portal from a wifi enabled device (cell, laptop, etc).  If prompted, the password is 'wled1234'.
9. Log into your wifi.
10. Switch back to your wifi, log into the wled UI, click Config, LED Prefrences, and use the following settings: in LED outputs: 1 = PWM RGB+CCT, GPIOs = 4, 12, 14, 13, 5.  Click Save.

Done!

## Issues?

Start a thread in one of these fantastic subreddits:

* [r/WLED](https://www.reddit.com/r/WLED)
* [r/HomeAutomation](https://www.reddit.com/r/homeautomation/)
* [r/HomeAssistant](https://www.reddit.com/r/homeassistant/)

## I don't trust your firmware

Neither do I... Please feel free to download them from source:

---

### WLED_0.14.0_ESP8266.bin

Download this from [Aircookie's WLED release page](https://github.com/Aircoookie/WLED/releases).  

Be sure to get the binary for the correct chipset.

Current direct download link for the ESP8266 which should work in the ESP8285: [https://github.com/Aircoookie/WLED/releases/download/v0.14.0/WLED_0.14.0_ESP8266.bin](https://github.com/Aircoookie/WLED/releases/download/v0.14.0/WLED_0.14.0_ESP8266.bin)

You will need to gzip this to reduce it's size.

---

### Tasmota-Minimal.bin.gz

I pulled mine right from the OTA page: [https://ota.tasmota.com/tasmota/release/](https://ota.tasmota.com/tasmota/release/)

Current direct download link: [https://ota.tasmota.com/tasmota/release/tasmota-minimal.bin.gz](https://ota.tasmota.com/tasmota/release/tasmota-minimal.bin.gz)

---

## Useful links I found along the way

This list will get expanded on

* LED Outputs: https://www.athom.tech/forum/strip-light-controller-bulb/wled-7w-bulb-gpio-configuration
* Anthem Tasmota product page with GPIOs: https://www.athom.tech/blank-1/color-bulb


