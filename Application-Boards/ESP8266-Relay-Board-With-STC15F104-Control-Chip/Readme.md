# Notes of the STC15F104 Controlled Relay board for ESP8266
-------------------------------------------------------------

Here are some important Info Links:

https://forum.arduino.cc/index.php?topic=473419.15

Specifically:
https://forum.arduino.cc/index.php?topic=473419.msg3367085#msg3367085

Datasheet for STC15F104:
http://www.stcmcu.com/datasheet/stc/STC-AD-PDF/STC15F101E-series-english.pdf


## Image of the Relay board

![Board Image](https://github.com/boseji/ESP-Store/tree/master/ESP8266-Relay-Board-With-STC15F104-Control-Chip/ESP8266-Relay-Board-With-STC15F104-Control-Chip.JPG)

## Running the Relay

In order to communicate with **STC15F104** chip from *ESP8266* we need the following:

  1. Communication Settings: 9600 BAUD, 1 Stop bit , 8bits data, No Parity<br>
  Fortunately this is the Basic configuration obtained for `Serial.open(9600);`
  
  2. Send Binary Sequence for **Turn ON** Command:<br>
```C
...
byte RlyON[]={0xA0,0x01,0x01,0xA2};
...
...
     // Need to Turn ON the Relay Now
     Serial.write(RlyON, sizeof(RlyON));
...
```
  3. Send Binary Sequence for **Turn Off** Command:<br>
```C
...
byte RlyOFF[]={0xA0,0x01,0x00,0xA1};
...
...
     // Need to Turn OFF the Relay Now
     Serial.write(RlyOFF, sizeof(RlyOFF));
...
```

## Example Program

This program will turn On and turn Off the relay continuously with a fixed interval.

```arduino

// Turn ON Command
byte RlyON[]={0xA0,0x01,0x01,0xA2};

// Turn Off Command
byte RlyOFF[]={0xA0,0x01,0x00,0xA1};

void setup() {
  delay(1000);
  Serial.begin(9600);
  delay(1000);
  Serial.println("Ready!");
}

void loop() {
  
  // Turn ON the relay for 1 Second
  Serial.write(RlyON, sizeof(RlyON));
  delay(1000);
  
  // Turn OFF the relay for 5 Seconds
  Serial.write(RlyOFF, sizeof(RlyOFF));
  delay(5000);
}
```
