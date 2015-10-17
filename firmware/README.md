# Firmware

This directory hosts the different pre-compiled and Factory firmware for *ESP8266 modules*.

## AT Command Firmware

This firmware gives the ability to interface / talk to the *ESP8266 modules* via `AT command` semantics. These are very familiar to the ones used for GSM / GPRS / 3G / 4GLTE / Modem world. 

Using this *AT Command Firmware* the ESP8266 module exposes a standard 2 wire(TX,RX) serial interface on its pins. There is possibility of storing boot time configuration such as WiFi network info and serial port configuration .etc. 

One needs an additional processing unit with *ESP8266 module* such as Arduino, mbed, Raspberry Pi or any other embedded processor / board to perform the actual function. The *ESP8266 module* only provides connectivity via WiFi or able to host a WiFi network using the **SoftAP** function.

##### The current release version from *Espressif Systems* is [AT_v0.50 based on esp_iot_sdk_v1.4.0][1].

The same has been updated in this directory [AT_v0.50_on_esp_iot_sdk_v1.4.0_150918.zip][2]

`MD5: acab782a4adc661f5c36f45555e24b08 AT_v0.50_on_esp_iot_sdk_v1.4.0_150918.zip`

`SHA1: 6af5c4a4af4cd27856837ccb1d4824dc1825a0c2 AT_v0.50_on_esp_iot_sdk_v1.4.0_150918.zip`


## [Node-MCU Firmware][3]

This is a Lua enabled firmware by the [Node-MCU team][4]. In this firmware the PC or Arduino or any other MCU can talk to the *ESP8266 module* via UART. The **Normal Baud rate** is generally `9600bps`. The programming and command interface on serial is via the [Lua Language][5].

Additionally this firmware provides **API** that helps to configure the *ESP8266 module* Wifi and I/O functions.

Below are a few examples of the programs that be run via serial connection:

##### Example of Configuring the Wireless network in Station Mode

```lua
wifi.setmode(wifi.STATION)
wifi.sta.config("SSID","password")
print(wifi.sta.getip())
--192.168.1.10
```

##### Example of GPIO Access and configuration

```lua
pin = 1
gpio.mode(pin,gpio.OUTPUT)
gpio.write(pin,gpio.HIGH)
gpio.mode(pin,gpio.INPUT)
print(gpio.read(pin))
```

##### Example of HTTP Server

```lua
-- a simple http server
srv=net.createServer(net.TCP) 
srv:listen(80,function(conn) 
    conn:on("receive",function(conn,payload) 
    print(payload) 
    conn:send("<h1> Hello, NodeMCU.</h1>")
    end) 
end)
```

##### Example of Ping to Google as HTTP Client

```lua
- A simple http client
conn=net.createConnection(net.TCP, false) 
conn:on("receive", function(conn, pl) print(pl) end)
conn:connect(80,"www.google.com")
conn:send("GET / HTTP/1.1\r\nHost: www.nodemcu.com\r\n"
    .."Connection: keep-alive\r\nAccept: */*\r\n\r\n")
```

And many more examples in the [Example Page of Node-MCU][6]

The updated [Node-MCU firmware 0.9.6-dev_20150704][7] is available under this directory.
There are two Variants based on the math computation being `float` or `integer`:

  * [nodemcu_float_0.9.6-dev_20150704.bin][8]
  `MD5: a1f6bab6e32651aa51aa10af4005ad82 nodemcu_float_0.9.6-dev_20150704.bin`
  `SHA1: be728ec30b45528c569853ab3bb695591a1e0e77 nodemcu_float_0.9.6-dev_20150704.bin`

  *  [nodemcu_integer_0.9.6-dev_20150704.bin][9]
  `MD5: 71f1a51d0eeaac43840a0aa8c8e02723 nodemcu_integer_0.9.6-dev_20150704.bin`
  `SHA1: 9b28451d09abffa4d678fda6517ee6ce56c4b1d3 nodemcu_integer_0.9.6-dev_20150704.bin`

Depending on the Processing Requirement one can choose either of them.



  [1]: <http://bbs.espressif.com/download/file.php?id=837>
  [2]: <https://github.com/boseji/ESP8266-Store/raw/master/firmware/AT_v0.50_on_esp_iot_sdk_v1.4.0_150918.zip>
  [3]: <https://github.com/nodemcu/nodemcu-firmware>
  [4]: <http://nodemcu.com/index_en.html>
  [5]: <http://www.lua.org/>
  [6]: <http://nodemcu.com/index_en.html#fr_5475f7667976d8501100000f>
  [7]: <https://github.com/nodemcu/nodemcu-firmware/releases/tag/0.9.6-dev_20150704>
  [8]: <https://github.com/boseji/ESP8266-Store/raw/master/firmware/nodemcu_float_0.9.6-dev_20150704.bin>
  [9]: <https://github.com/boseji/ESP8266-Store/raw/master/firmware/nodemcu_integer_0.9.6-dev_20150704.bin>
