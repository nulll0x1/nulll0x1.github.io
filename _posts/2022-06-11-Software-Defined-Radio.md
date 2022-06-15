
In this blog post, We will examine the world of Software Defined Radio (SDR) and its application in penetration testing and use by attackers. We'll look at a quick overview of the technology and background as well as several options for SDR hardware, followed by several software options for interacting with SDR hardware.

We Introduce The Following Topics to be covered: 

- Background
- Choosing an SDR
- Visualization
- FCC ID
- Car Keys

## Background

### **What is Software Defined Radio?**

Software Defined Radio (SDR) is a platform where developers can write software to process and interpret signals received from the RF spectrum instead of developing modulation mechanisms in hardware. Traditional wireless devices, such as Wi-Fi cards, Bluetooth adapters, GSM receivers, and other proprietary systems are designed to be cost-effective and limit accessibility into the wireless spectrum while providing the functionality needed for the product design. 
By contrast, SDR technology does not make any assumptions as to how the user wishes to interpret the spectrum for receive or transmit paths. 
In the commodity SDR hardware available for purchase today, the end-user has access to a wide range of frequencies, from 1 MHz all the way to 5.9 GHz, depending on the SDR selected.

### **Generic SDR Block Diagram**

![SDR](/images/SDR.png?style=centerme)

Generically, the SDR hardware interacts with a host system over a USB 2.0, 3.0, or Ethernet connection, depending on SDR selection. Connecting to a Field Programmable Gate Array (FPGA) that includes software for encoding signal information into binary format, the FPGA interacts with a number of analogs to digital Generic SDR Block Diagram converters (ADC) and a number of digital to analog converters (DAC). The ADCs and DACs connect to a variety of receive and transmit frontends.

For the process of demodulating traffic, a piece of host software running on PC hardware will tune the receiving board to a given frequency and gain level. When a signal is received, it is passed to the ADCs that feed the data to the FPGA. 

### Usage

Many organizations use proprietary, or nonstandard, wireless technologies (that is, not the Wi-Fi or Bluetooth that we have come to expect in our environments) but often miss the fact that there is or may be some risk of exposure in their use. Knowing and auditing these wireless systems eventually becomes an essential part of a comprehensive wireless security program.

With Software Defined Radio we have the potential to find vulnerabilities in wireless implementations that were previously unknown and pose risks to the organization. 

## Choosing an SDR

Because of the Variety of SDR Platforms, It is hard to choose the right SDR for the right job. 
Many decisions can affect your selection:

- Tx capable, or Rx only
- Bandwidth for Rx/Tx
- Cost
- Tool capability and ease of use


Tx Capable SDRs have Great Power (and Great Responsibility)

![SDR](/images/SDR%201.png?style=centerme)

SDR Transceivers are able to both transmit and receive radio signals. in other words, Rx (Receive) and Tx (Transmit) are Capable. 

### **HackRF one**

HackRF One is a Software Defined Radio (SDR) peripheral capable of transmission or reception of radio signals from 1 MHz to 6 GHz, designed to enable the test and development of modern and next-generation radio technologies. HackRF One covers many licensed and unlicensed ham radio bands. HackRF One is an open-source hardware platform that can be used as a USB peripheral or programmed for stand-alone operation.

![SDR](/images/SDR%202.png?style=centerme)

HackRF One works as a sound card of the computer. It processes Digital Signals to Radio waveforms allowing the integration of large-scale communication networks. It is designed to test, develop, improvise, and modify the contemporary Radio Frequency systems.

- Rx and Tx enabled, 300$
- Half-Duplex, 1 MHz–6 GHz, 20 MHz Bandwidth
- Open Source, Huge Community Support
- Adds-On
    - CCC Rad1o
    - Portapack

### YARD Stick One

YARD Stick One (Yet Another Radio Dongle) can transmit or receive digital wireless signals at frequencies below 1 GHz. It uses the same radio circuit as the popular IM-Me. 
The radio functions that are possible by customizing IM-Me firmware are now at your fingertips when you attach YARD Stick One to a computer via USB.

![SDR](/images/SDR%203.png?style=centerme)

YARD Stick One comes with RfCat firmware installed, courtesy of atlas. RfCat allows you to control the wireless transceiver from an interactive Python shell or your own program running on your computer. YARD Stick One also has CC Bootloader installed, so you can upgrade RFCat or install your own firmware without any additional programming hardware.

### BladeRF

Another Software Defined Radio (SDR) is capable of transmission or reception of radio signals from 300 MHz to 3.8 GHz. 
Currently, two models are available from Nuand, both of which had their first availability at 
DEF CON 21 in August 2013. All models feature the ability to do **Full-Duplex Tx and Rx**. Both BladeRF models are available via small production runs. The BladeRF also features a wider Tx/Rx bandwidth than some the lower-price options.

The BladeRF has an active support community but less so than the HackRF and, as a
the result, more-limited support with some of the popular SDR tools.

![SDR](/images/SDR%204.png?style=centerme)

One added benefit of the BladeRF is the nearly out-of-the-box support for OpenBTS and OpenLTE without the alleged need to purchase an external clock source (at about $300). This means one could leverage this device out of the box to man in the middle and/or provide cellular service, and at a reasonable price.

### **Antenna Length**

In order to have the most efficient reception and transmission, it is important to have the antenna tuned for the desired frequency range. This length is determined by the frequency, and therefore the RF wavelength is based on a specific formula: The total length of the antenna in meters is equal to 300 divided by the frequency in MHz, Divided by 100. 

![SDR](/images/SDR%205.png?style=centerme)

For reception (RX), any random length antenna will work, but it will not be as efficient as a properly tuned antenna.

For transmit (TX), antenna length is extremely important. An antenna used for TX that is too long is highly inefficient resulting in significantly reduced range for the reception. However, if an antenna is too short during transmission, the RF energy trying to “escape” from the antenna cannot be efficient, and the antenna captures the remaining energy from the wave, folding it back towards the transmitter instead of in the air.

If, during transmission, an antenna is too short and the resulting VSWR (Voltage standing wave ratio) is too high RF energy is reflected back to the transmitter. This reflection, depending on power and duration can permanently damage the transmitter.

## Visualization

Because wireless signals, represented as radio frequency (RF) energy, are colorless, tasteless, and odorless, it can be very difficult for us as humans to detect their presence. However, by using the capabilities of an SDR device, we can use the full bandwidth of an SDR receive function to convert the presence and strength of RF energy to a visual representation, making it easier to observe and locate in the spectrum. 

There are a lot of tools that can make interacting with RF signals easy. We introduce you to multiple options you can choose from. 

- GQRX
- GNU Radio
- Universal Radio Hacker

Of Course, There are a lot of tools does the same job but we recommend using URH, In a similar fashion to GQRX, Universal Radio Hacker (URH) can load samples and display the waveform transition over time, but with significantly more features. At the outset, URH can obtain samples directly from an appropriate SDR.

![SDR](/images/SDR%206.png?style=centerme)

While we can also recover the symbols per second on a transmission with URH, we can also apply several basic methods of demodulation and decoding, in order to recover the binary for a transmission, which can be converted to the text where appropriate. Additionally, the conversion to binary can be modified and retransmitted with an appropriate SDR or RFcat dongle. 

Overall, URH features far eclipse thanks to AI detection that makes the process of data recovery, modification, and re-transmission easier. 

## From RF Signal to Bytes

In Radio Communication systems, the information is carried across space using radio waves. at the end of sending, the information is converted by a Transducer (Converts Signal from one form of energy to another form of signal). 

![SDR](/images/SDR.gif?style=centerme)

The Process of Taking an RF Transmission and turning it back into something readable/understandable by Humans or Computers is quite challenging. In order to start this process and “Translate” the unknown signals, We have to answer several questions and perform several actions to recover data: 

- Frequency Used?
- What was The modulation type? (in order to determine what was the waveform used to carry data)
- What was the encoding type? (in order to determine how the spacing of the waveform was used to indicate data)
- Converting demodulated and decoded data to binary (Computer Readable)
- Determine the meaning, format, and protocol that the recovered binary data represents (Human Readable)

## FCC ID

FCC ID is a unique identifier assigned to a device registered with the United States **Federal Communications Commission** For the legal sale of wireless devices in the US, 
manufacturers must Have the device evaluated by an independent lab to ensure it conforms to FCC standards. Provide documentation to the FCC of the lab results, Provide User Manuals, Documentation, and Photos relating to the device. Digitally or physically label the device with the unique identifier provided by the FCC. 

![SDR](/images/SDR%207.png?style=centerme)

If we [Looked up](https://fccid.io/) the FCC-ID printed on the back the of Key we will see a lot of useful information.
 

![SDR](/images/SDR%208.png?style=centerme)

From The FCC website, we extract nearly all the questions we have been asking and more useful data. 

- The Key is transmitting at 315MHz
- Using ASK Modulation (**[Amplitude Shift Keying](https://www.tutorialspoint.com/digital_communication/digital_communication_amplitude_shift_keying.htm)**)

and a lot of other helpful information about that device, User Manuals, Test Reports, RF-Exposure, and its manufacture. 

## Car Keys

A **Remote Keyless System** (**RKS**), also called **Keyless Entry** or **Remote Central Locking**, is Widely used in automobiles, an **RKS** performs the functions of a standard car key without physical contact. When within a few yards of the car, pressing a button on the remote can lock or unlock the doors, and may perform other functions. 
A remote keyless system can include both *remote keyless entry* (RKE), which unlocks the doors, and *remote keyless ignition* (RKI), which starts the engine.

After Pressing the button that unlock the doors, The key sends a coded secret to the car using the Radio Waves, and if you have an **SDR** you can record this message and **Replay** it again to unlock the doors anytime. 

![SDR](/images/SDR%201.gif?style=centerme)

GIF above explains the idea of Capturing and Replaying back showing that is easy and accessible by anyone with 300$ SDR. Because of that, Car Manufactures Provided a solution called **Rolling Codes**. 

## Rolling Codes

Rolling Codes is Used in Keyless Entry Systems to prevent replay attacks, where an eavesdropper
records the transmission and replays it at a later time to cause the receiver to 'unlock'.

Remote control systems use a rolling code that changes itself for every use. An attacker may be able to learn the code word that opened the door just now, but the receiver will not accept that code word anymore in the future. A rolling code system uses encryption methods that allow the remote control and the receiver to share codewords but make it difficult for an attacker to break the encryption.

![SDR](/images/SDR%209.png?style=centerme)

In 2015, Security Researcher Samy Kamkar Found **Rolljam Vulnerability**; ****The device transmits a jamming signal to block the vehicle's reception of rolling code signals from the owner's fob, while recording these signals from both of his two attempts needed to unlock the vehicle. 
The recorded first code is forwarded to the vehicle only when the owner makes the second attempt, while the recorded first code is retained for future use.