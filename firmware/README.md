# Firmware

This directory hosts the different pre-compiled and Factory firmware for *ESP8266 modules*.

## AT Command Firmware

This firmware gives the ability to interface / talk to the *ESP8266 modules* via `AT command` semantics. These are very familiar to the ones used for GSM / GPRS / 3G / 4GLTE / Modem world. 

Using this *AT Command Firmware* the ESP8266 module exposes a standard 2 wire(TX,RX) serial interface on its pins. There is possibility of storing boot time configuration such as WiFi network info and serial port configuration .etc. 

One needs an additional processing unit with *ESP8266 module* such as Arduino, mbed, Raspberry Pi or any other embedded processor / board to perform the actual function. The *ESP8266 module* only provides connectivity via WiFi or able to host a WiFi network using the **SoftAP** function.

##### The current release version from *Espressif Systems* is [AT_v0.50 based on esp_iot_sdk_v1.4.0][1].

The same has been updated in this directory [AT_v0.50_on_esp_iot_sdk_v1.4.0_150918.zip][2]

  [1]: <http://bbs.espressif.com/download/file.php?id=837>
  [2]: <https://github.com/boseji/ESP8266-Store/raw/master/firmware/AT_v0.50_on_esp_iot_sdk_v1.4.0_150918.zip>
