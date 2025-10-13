---
title: Tools of Trade
layout: home
nav_order: 1
has_toc: false # on by default
has_children: false
comments: true
usetocbot: true
---

# {{ page.title }}
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---


## Installation of IDE 
The very first step for labs today is installation of the interactive development envirnoment you are going to use for the coding.  You can download Thonny from [here](https://thonny.org/).

<video controls width="400">
  <source src="./global_assets/thonnyinstall.webm" type="video/webm" />
</video>

## Flashing MicroPython Software
Connect ESP32S3 with Bootloader mode: Press and hold down the BOOT button while connecting the board with a type-C USB cable provided to the computer. After connecting, let go of the BOOT button.

Then you can continue through either **Thonny** or using **Command Line**.

<!-- ![Screenshot of Board](./global_assets/esp32s3_global_assets/board.png) -->
<p align="center">
  <img src="./global_assets/esp32s3_global_assets/board.png" alt="System Overview" width="70%">
</p>

### Flashing Through Thonny
1. Open Thonny and click the right bottom as below and you should see a **configure interpreter**. Then enter configure interpreter.
![Enter configure interpreter](./global_assets/esp32s3_global_assets/EnterConfigureInterpreter.png)
2. Select interpreter kind as MicroPython(ESP32), and the Port of WebREPL as the usbmodem101 or anything like it. For windows the port can be named as COM3 or anything like it. Then click **Install or update MicroPython (esptool) (UF2)** can be found at the right bottom.
![configure interpreter](./global_assets/esp32s3_global_assets/ConfigureInterpreter.png)
3. Then select options as the figure below. Note that the Target port can be different. You may need to select any looks like the one in the figure. Then click Install to erase and install firmware into ESP32S3.
![install micropython](./global_assets/esp32s3_global_assets/installmicropython.png)

### Using Command Line
After completing the installation of the Thonny IDE, our next step is completing the installation of Micropython firmware on the XIAO ESP32S3 Board. Follow the following step to accomplish this task:
1. Launch MicroPython [website](https://micropython.org/).
2. Click on [Download](https://micropython.org/download/) option from Navigation Menu.
3. The Download page shows, various different MCUs for which MicroPython is available. From MCU section click on esp32s3.
![MicroPython Website](./global_assets/esp32s3_global_assets/mpythoninstall.png)
4. From options select ESP32-S3 Espressif.
![Screenshot of Website](./global_assets/esp32s3_global_assets/ESP32S3.png)
5. The page should now show all the releases. From Releases section, select the latest release this is indicated in bold and is the first item on the list. 
6. Click the link to download the firmware file named with the end of ".bin".
7. Now we can find the device we just connected from our computer. To find the device, we need to check the Port Name through either way from below:
    - **Windows**: open "Device Manager-->Serial Port", there should be a device with the named of **"COMX"**, X can be a figure, e.g., "COM3" or "COM4".
    - **MacOS & Linux**: on your terminal try command
        - `ls /dev/cu*` for MacOS
        - `ls /dev/ttyS* /dev/ttyUSB*` for Linux
8. Download **esptool**, a tool for erasing and writing firmware to your ESP32S3. To download it, open your Command Line or Terminal and try `pip install esptool`. Then, try `esptool -h` or `esptool.py -h` to see if esptool is ready.
9. Now we need to use esptool to erase the flash in ESP32S3 and write the firmware into ESP32S3. NOTE THAT, to use these command, you need to find the **Port Name** and **Bin File** and replace the commands below with your actual ones. For example, let's say I found my port name is `/dev/cu.usbmodem1101` and my bin file is `ESP32_GENERIC_S3-20250911-v1.26.1.bin`. Then I type this down, 
  ``esptool.py --chip esp32s3 --port /dev/cu.usbmodem1101 --baud 460800 write_flash -z 0x0 ESP32_GENERIC_S3-20250911-v1.26.1.bin``
    1. **Erase**: 
    ``esptool.py --chip esp32s3 --port [Port Name] erase_flash``

    2. **Write**: 
    ``esptool.py --chip esp32s3 --port [Port Name] --baud 460800 write_flash -z 0x0 [Bin File]``

## Thony IDE Tutorial
Once you have got the MicroPython firmware on the board, you can use REPL prompt in Thonny to test Python Commands. The video below gives a quick walkthrough of basic features.

<video controls width="400">
  <source src="./global_assets/thonnyUsage.webm" type="video/webm"/>
</video>

Some other places to find detailed account of IDE features include:
1. Thonny's own website and Introductory [Video](https://www.youtube.com/watch?v=nwIgxrXP-X4)
2. Random Nerd's [Page](https://randomnerdtutorials.com/getting-started-thonny-micropython-python-ide-esp32-esp8266/) which is for different processor but same steps really.
3. ESP32S3 [Guidance](https://projects.raspberrypi.org/en/projects/getting-started-with-the-pico/2).
<!-- 4. Micropython [Book](./global_assets/book.pdf) from Raspberry Pi Foundation. -->


<!-- ## Board Details and Relevant Documents
All relevant documents is below:
1. Product [Page](https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/) by SeeedStudio. -->