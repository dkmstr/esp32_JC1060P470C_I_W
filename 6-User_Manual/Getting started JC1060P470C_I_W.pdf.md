|                  | Welcome | to the | JCZN     | Workshop!        |     |     |
| ---------------- | ------- | ------ | -------- | ---------------- | --- | --- |
|                  | Table   | of     | contents |                  |     |     |
| •••••••••••••••• |         |        |          | •••••••••••••••• |     |     |
一、Introduction••••••••••••••••••••••••••••••••••••••2
IDE••••••••••••••••••••••••2
| 二、Installing | using   | Arduino                             |     |     |         |      |
| ------------ | ------- | ----------------------------------- | --- | --- | ------- | ---- |
| 三、sample     | program | usage••••••••••••••••••••••••••••11 |     |     |         |      |
|              |         | http://www.jczn1688.com/            |     |     | 第 1 ⻚ 共 | 12 ⻚ |

Getting Started
Introduction
The objective of this post is to explain how to upload anArduino program to the JC1060P470 module,
fromJCZN.
http://www.jczn1688.com/zlxz
The ESP32-P4 is powered by a dual-core RISC-VCPU featuring AI instruction extensions, an advanced
| memory | subsystem, andintegratedhigh-speedperipherals. |     |     |     |     |     |
| ------ | ---------------------------------------------- | --- | --- | --- | --- | --- |
Powered by a dual-core RISC-V CPU running at speeds up to 400 MHz, the ESP32-P4 also boasts
| supportfor | single-precision | FPU andAI | extensions,providing | essential |     |     |
| ---------- | ---------------- | --------- | -------------------- | --------- | --- | --- |
ESP32-P4 itself does not have WiFi and Bluetooth functions. Use ESP-Hosted to connect to the
| ESP32-C6wirelessSOCthrough |               | the | SDIO/SPI/UARTinterface. |     |     |     |
| -------------------------- | ------------- | --- | ----------------------- | --- | --- | --- |
| Installing                 | using Arduino | IDE |                         |     |     |     |
| Programmingthe             | ESP32         |     |                         |     |     |     |
An easy way to get started is by using the familiar Arduino IDE. While this is not necessarily the best
environment for working with the ESP32, it has the advantage of being a familiar application, so the
learning curveisflattened.
| Wewillbeusing | theArduino       | IDE forourexperiments. |     |     |     |     |
| ------------- | ---------------- | ---------------------- | --- | --- | --- | --- |
| 1，Installing  | using ArduinoIDE |                        |     |     |     |     |
wefirstneedtoinstallversion 2.3.4oftheArduino IDE (orgreater),forexample,theArduino installation
wasin “C/Programs(x86)/Arduino”.
downloadreleaselink:
https://www.arduino.cc/en/software
|     |     |     | http://www.jczn1688.com/ |     | 第 2 ⻚ 共 | 12 ⻚ |
| --- | --- | --- | ------------------------ | --- | ------- | ---- |

2，Thisis the waytoinstall Arduino-ESP32directly fromthe ArduinoIDE.
Add BoardsManagerEntry
Hereiswhatyou need todo toinstall theESP32 boardsinto the Arduino IDE:
| （1） Open   | the Arduino  | IDE.          |      |     |     |
| ---------- | ------------ | ------------- | ---- | --- | --- |
| （2）Clickon | the Filemenu | on thetopmenu | bar. |     |     |
（3）Clickon the Preferencesmenu item.This willopen aPreferencesdialogbox.
|     |     |     | http://www.jczn1688.com/ | 第 3 ⻚ 共 | 12 ⻚ |
| --- | --- | --- | ------------------------ | ------- | ---- |

（4）Youshould beon the Settingstabinthe Preferencesdialog boxbydefault.
| （5）Look | forthe textbox | labeled“AdditionalBoards |     | ManagerURLs”. |     |     |
| ------- | -------------- | ------------------------ | --- | ------------- | --- | --- |
（6）If thereisalready textin thisboxaddacoma atthe endofit,then followthenext step.
| （7）Paste      | the following | linkinto | the text box ： |     |     |     |
| ------------- | ------------- | -------- | -------------- | --- | --- | --- |
| Stablerelease | link:         |          |                |     |     |     |
https://espressif.github.io/arduino-esp32/package_esp32_dev_index.json
| （8）ClicktheOK  | buttontosave |        | thesetting.              |     |         |      |
| -------------- | ------------ | ------ | ------------------------ | --- | ------- | ---- |
| Thetextboxwith | theJSON      | linkin | itis illustratedhere:    |     |         |      |
|                |              |        | http://www.jczn1688.com/ |     | 第 4 ⻚ 共 | 12 ⻚ |

| (9)In theArduino  | IDE      | clickonthe  | Toolsmenu       |     | on the       | top menu bar. |     |     |
| ----------------- | -------- | ----------- | --------------- | --- | ------------ | ------------- | --- | --- |
| (10) Scrolldown   | tothe    | Board:entry |                 |     |              |               |     |     |
| (11) Asubmenuwill | openwhen |             | youhighlightthe |     | Board:entry. |               |     |     |
(12) Atthetop ofthe submenuisBoardsManager.Click onitto open theBoards Managerdialog box.
| (13)I nthe search | boxinthe |     | Boards Managerenter |     | “esp32”. |     |     |     |
| ----------------- | -------- | --- | ------------------- | --- | -------- | --- | --- | --- |
(14) You should see an entry for “esp32 by Espressif Systems”. Highlight this entry and click on the
Install button.
| ThiswillinstalltheESP32 |     | boardsintoyour |                          | Arduino | IDE |     |         |      |
| ----------------------- | --- | -------------- | ------------------------ | ------- | --- | --- | ------- | ---- |
|                         |     |                | http://www.jczn1688.com/ |         |     |     | 第 5 ⻚ 共 | 12 ⻚ |

Once the installation completes, we need to select the correct board options for the "ESP32 Arduino"
board.Inthe board type,in thetoolstab,wechoose “ESP32P4DevModule”.
| SetandIn | the programmerentry | ofthe same               | tab,we choose“esptool”. |         |      |
| -------- | ------------------- | ------------------------ | ----------------------- | ------- | ---- |
|          |                     | http://www.jczn1688.com/ |                         | 第 6 ⻚ 共 | 12 ⻚ |

It’s important to note that after the code is uploaded, the device will start to run it. So, if we
want to upload a new program, wee need to reset the power of the device, in order to
| guarantee | that it enters | flashing mode | again. |     |     |
| --------- | -------------- | ------------- | ------ | --- | --- |
First program
Sincethisplatformisbased onArduino, we canusemanyofthe usualfunctions. Asanexampleforthe
firstprogram,thecodebellow startsthe Serialportandprints“hello fromESP32”every second.
|     |     | void setup() { |     |     |     |
| --- | --- | -------------- | --- | --- | --- |
Serial.begin(115200);
}
void loop(){
Serial.println("hellofromESP32");
delay(1000);
}
Ifeverything is working fine, we will see the output in the serial console shown.
|     |     | http://www.jczn1688.com/ |     | 第 7 ⻚ 共 | 12 ⻚ |
| --- | --- | ------------------------ | --- | ------- | ---- |

Again thankyou forsomuch concern..Hopefully, it'sthebeginning ofawonderful relationship!
| Sample | program | usage |     |     |     |
| ------ | ------- | ----- | --- | --- | --- |
At present, only a preliminary explanation and introductory use are given to the samples displayed on
thescreen, andthe corresponding examplesinthe datacenterare found,asshown in thefigure：
OpenthelibrarymanagerinArduino,searchforlvgl,andclickinstal.
|     |     |     | http://www.jczn1688.com/ | 第 8 ⻚ 共 | 12 ⻚ |
| --- | --- | --- | ------------------------ | ------- | ---- |

Findthe datacenter1_1_Lvgl_v8
Asshown：
Downloadonelibrary files.
Lvgl，>v8.3.0
| http://www.jczn1688.com/ | 第 9 ⻚ 共 | 12 ⻚ |
| ------------------------ | ------- | ---- |

Copythelv_conf.h ofthe datacenter.
Asshown：
Put thisfile underthearduinolibrary file,itmust bein thesamerootdirectory asthe library lvgl.
Asshown：
| http://www.jczn1688.com/ | 第 10 ⻚ | 共 12 ⻚ |
| ------------------------ | ------ | ------ |

| Three-Lvgldemos | Thefile iscopiedto | theSRCfolder |     |     |
| --------------- | ------------------ | ------------ | --- | --- |
Asshown：
|     |     | http://www.jczn1688.com/ | 第 11 ⻚ | 共 12 ⻚ |
| --- | --- | ------------------------ | ------ | ------ |

| After compiling, | you can run | LVGL and                 | touch normally. |        |        |
| ---------------- | ----------- | ------------------------ | --------------- | ------ | ------ |
|                  |             | http://www.jczn1688.com/ |                 | 第 12 ⻚ | 共 12 ⻚ |