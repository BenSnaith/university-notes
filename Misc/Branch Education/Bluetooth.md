Bluetooth uses an 123mm wavelength in order to transmit information.

When communicating with a device, the master device transmits a wave of 121mm for a 1 and 124mm for a 0, the smartphone antenna generates these wavelengths and can switch between around 1 million times per second, thus 1 million bits per second, the antenna inside of the slave device has been specifically designed to receive and transmit these specific wavelengths back and forth.

Electromagnetic waves travel out like a massive expanding sphere in all directions.

  

**2.4 - 2.4835 GHz Bandwidth.**

  

How to deal with so many Bluetooth devices being used in one space.

The section of the 2.4-2.4835 Bandwidth is split up into 79 difference channels, with each having a specific wavelength for a 1 and another for a 0. at any given moment your master and slave device communicate across any one of the given channels.

  

**How does the slave device receive data from your master device specifically.**

  

Messages are assembled into packets, the first 72-bits contain the access code that synchronizes your master and slave device to make sure it’s the specific devices, this access code is like the address on a package, the next 54-bits are the header which provides details of the information being sent, this is like knowing the size of the letter of dimensions of the box, the last 500 bits is the actual information or the payload, be that the data for the audio etc.

  

**More complexity**

  

When your master and slave communicate, the do not stick to a single channel, but hop around to many of the 79 channels, this is called the Frequency-Hopping Spread Spectrum and it happens 1600 times per second, after each hop, one packet of information containing the **Access codes, Header and Payload** is sent between the master and slave device. The master dictates which channels it’s gonna hop to and when, and the slave just follows it, if one of the channels is too busy the master device will adapt and not use that channel until the noise clears, this **Channel Hopping** also prevents anyone from eavesdropping on any of data being transmitted because only your master and slave know the channels that they will switch to.

Because the information is split up into thousands of packets, if the slave didn’t receive a certain packet it will tell the master that it did not receive it and the master will send that specific packet again.

  

**Noise in a 2.4Ghz spectrum**

  

The wavelength of 2.4 - 2.4835Ghz is shared by many devices, for example your microwave is in this range and has a frequency of 2.45Ghz in fact when your microwave is on it can cause your slave to lose track of the information being send by the master or in other words can lose signal.

2.4Ghz WI-FI modems also operate in this range of the spectrum, similar to Bluetooth WIFI modems also divide this range up into 14 different channels in order the accommodate multiple users.

  

**What is there are loads of devices; Modems, Microwaves, Phones, Headphones, sharing the same frequency range.**

  

The devices get around this through

- Frequency hopping
- Packets
- Error detection
- Noise filtering

Done on a Bluetooth microchip.

  

**Even more complication**

  

Frequency-Shift Keying, is the scheme of sending a binary set of 1’s and 0’s by transmitting different frequencies of electromagnetic waves.

Frequency-shifting means that we adjust the frequency, and keying means that a 1 is assigned to one frequency and a 0 to another.

The master emits a carrier wave and the frequency is shifted depending on which wave needs to be sent, the waves get thinner or wider respectively, this shifting of frequencies in order to send data is also called frequency modulation and is closely related to FM radio. Bluetooth isn’t limited to just using FSK but rather it can use other properties of electromagnetic waves to transmit information.

A different method that has higher data transfer rates is called phase-shift keying which is significantly more complicated.

A electromagnetic wave’s phase is a property that our eyes cannot perceive.

**The frequency remains the same, but it’s like we make small chops to the waves and inside of the waves so they are slightly out of sync.**

The master and slave device can be designed to emit and detect shifts in phase of an electromagnetic wave and binary values can be keyed to different levels of shift in the phase of the wave.

  

The slave can send information packets back to the master.

e.g if you are on the phone using Bluetooth headphones the microphone data can be sent as packets back to the master device.

In order for Bluetooth to accommodate this transmission the master and slave alternate transmitting and receiving data. while maintaining the frequency hop schedule

|   |   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|---|
|Master Transmit|Master Receive|Master Transmit|Master Receive|Master Transmit|Master Receive|Master Transmit|Master Receive|Master Transmit|Master Receive|
|Slave Receive|Slave Transmit|Slave Receive|Slave Transmit|Slave Receive|Slave Transmit|Slave Receive|Slave Transmit|Slave Receive|Slave Transmit|
|Channel 13 (n)|Channel 71 (n)|Channel 68 (n)|Channel 2 (n)|Channel 43 (n)|Channel 55 (n)|Channel 41 (n)|Channel 9 (n)|Channel 29 (n)|Channel 33 (n)|
|625 microseconds|625 microseconds|625 microseconds|625 microseconds|625 microseconds|625 microseconds|625 microseconds|625 microseconds|625 microseconds|625 microseconds|

  

The size of the payload, specified by the header can vary from 136-bits to 8168-bits depending on the requirements of the data.

For example simple commands like; play, pause, skip. would require very few bits.

Where as sending high quality audio would require a lot more bits.