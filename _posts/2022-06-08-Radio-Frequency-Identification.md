Introducing RFID cards Technology, How it Works, and How Attackers can Exploit Weaknesses Acheiving Their Operation. Leaving you with a Good Background About This Technology. 

Headlines Would be Covered as the following: 

- Background and introduction
- Classes and Standards
- Encoding Schemes/Mechanisms
- Demodulation and Decoding Schemes/Mechanisms
- Cloning Cards
- Achieving Long Range Reads

## Usage

RFID stands for Radio Frequency Identification, it is Everywhere, You Probably Use one of these cards almost every day. 

- Access Control
- Tickets
- E-Wallets
- Ski Pass
- Loyalty Cards
- Toys, and More...

## Background

Radio Frequency Identification or RFID Uses an Electromagnetic Field to Automatically Identify and Track Tags Attached to Objects.

There are Different RFID Standards, Frequencies, Vendors, and Usages. But There are Two Main Types of RFID Cards. 

### Active Cards

Active Cards have a built-in Battery, The power source is used to run the microchip's circuitry and broadcast the signal back to the reader.

<img src="/images/Untitled.png" alt="fig.1: Built-in Battery Active Card" width="600"/>

Commonly used as "**beacons" *to accurately track the real-time location of assets or in high-speed environments such as tolling**.*

**Beacons**, on the other hand, emit a signal at a pre-set interval. This type of active tag is used in real-time location systems (RTLS) for tracking anything from wheelchairs at a hospital to large cargo containers at a shipping dock. 

![fig.2: Data Transfer between the tag and the reader.](/images/Untitled%201.png?style=centerme)

Active tags provide a much longer read range than passive tags, but they are also more expensive.

Operates Between **433 MHz - 5.8 GHz** 

### Passive Cards

- Smaller Tags
- Much Cheaper
- Thinner/More Flexible
- Variety  of designs
- Tags Can Last a Lifetime Without a Battery

![fig.3: Different Sizes, Shapes, and Flexibility, Same Functionality.](/images/Untitled%202.png?style=centerme)

Operates Between 

- **(125-134 kHz)** known commercially as **Low-Frequency Cards**,
- **(13.56MHz)** known commercially as **High-Frequency Cards**,
- **(860-915MHz)** known commercially as **Ultra-high-frequency** Tags.

### How Passive Cards Works

![fig.4: Passive RFID Card](/images/Untitled%203.png?style=centerme)

The Communication between the card and the reader is very simple; Whenever The card is near enough to the reader -Energy-, There is an Electromagnetic Filed Caused to cut throw the copper (inside the Card) and transfer a small amount of energy, enough to power up the Chipset that holds the data (Unique ID). The Reader works at the same frequency as receiver so it can Read the signal of 1's and 0's, Passing it to The Company's Database to check it's authenticity; If That Unique ID number matches, then this card is authorized and the Gate will open. 
if not, The Gate Will Not open.   

![fig.5: Data Exchange Between The Card and The Receiver](/images/Untitled%204.png?style=centerme)

---

## Classes and Standards

### Low Frequency (LF) RFID Cards

Operate in the 30 kHz to 300 kHz Range, and Have a Read Range up to 10cm. Shorter Read Range and Slower Data Read Rate than Other Technologies, But they perform better in liquid or metal presence, which can cause interference with other types of RFID tag transmission. 
Popular LF RFID Standards include ISO 14223 and ISO/IEC 18000-2. 

- Low Price Range
- Used in a lot of access control systems
- Lack of Security Features

### High Frequency (HF) RFID or NFC Cards

Operate in the 3MHz to 30MHz range (Commonly 13.56MHz), Providing a reading distance of 
10 cm to 1M. Common applications include electronic ticketing and payment and data transfer. 
Near Field Communication (NFC) technology Used for payment cards and hotel key card applications; NFC is actually High Frequency RFID with added security protocols.  
Other types of smart card and proximity card payment and security systems also use High Frequency Range. 
Standards include ISO 15693, ECMA-340, ISO/IEC 18092 (for NFC), ISO/IEC 14443A and 
ISO/IEC 14443 (for MIFARE and other Smart Card Solutions).

### Ultra-High Frequency (UHF) RFID Tags

Operate in the range between 300 MHz and 3 GHz, offer read ranges up to 12 m, and have faster data transfer rates. They are more sensitive to interference from metals, liquids, and electromagnetic signals, but new design innovations have helped mitigate some of these problems.
UHF tags are much cheaper to manufacture, and as such are commonly used in retail inventory tracking, smart cities, pharmaceutical anti-counterfeiting, and other applications where large volumes of tags are required. The EPCglobal Gen2/ISO 18000-6C standard is a well-known global standard for item-level tracking applications.

---

# EM4100

Probably the cheapest tag on market by EM Microelectronic, Very common especially in low-end devices like:

- Intercoms,
- Parking gates
- Time attendance, etc.

Operates at **125KHz Low Frequency** and has 64-bit of **Read-Only** Memory.  

### **Reading an EM4100 RFID Transponder**

EM4100 compatible RFID transponders (Card) carry 64 bits of Read-Only memory. This means that information can be read from the Tag but no data can be changed, or written into the card once the card has been programmed with the initial data. 
The format of the data is as shown here.

![fig.6: Transponder Block Memory.](/images/Untitled%205.png?style=centerme)

When the Tag enters the electromagnetic field transmitted by the RFID reader it draws power from the field and will commence transmitting its data as shown above. 
The first 9 bits are a logic 1. These bits are used as a marker sequence to indicate the beginning of the string.  As Even parity is used throughout the data this 9-bit sequence of 1's will not occur at any other location in the string.  This is followed by 10 groups of 4 data and 1 even parity bits. Finally, there are 4 bits of column parity (Even) and a stop bit (0). The Tag then continues to repeat this string as long as it has power. 

Shown here is an example string for a proximity card that has the data $06 (version number), and $001259E3 as a data string.

![fig.7: Proximity Card and Data Distribute. ](/images/Untitled%206.png?style=centerme)

### Data Modulation

The RFID transponder is able to transmit its data by modulating the RF field of the Reader. Here we discuss 3 popular modulation schemes.

- Manchester Encoding.
- BiPhase Encoding.
- PSK Encoding.

The Transponder and Reader use the individual cycles of the RF field to synchronize the data transmission between the two. The frequency of the synchronizing clock then simply becomes the frequency of the RF field used. 
RFID system clock frequencies vary according to the application required.  
In low frequency, short distance sensing of Tags the typical band used is between 100-150Khz. 
For longer-range sensing a system frequency of 13.56Mhz might be used, or other frequency as the application requires.

Of course, the designer of an RFID system is restricted to using particular frequency bands as RFID systems are radio emitting devices and therefore under the control of the local radio frequency regulator bodies.

The length of each bit is specified in terms of clock cycles. For the EM4100 protocol bit lengths can be either 64, 32, or 16 Clock cycles.

### Manchester Encoding Scheme

Manchester Encoding schemes modulate the RF filed Producing a level transition in the middle of the bit period. A low to high transition represents a logic 1 state, high to low transition represents a logic 0 state. 

![Untitled](/images/Untitled%207.png?style=centerme)

**Encoding Mechanism**

- A 0 is expressed by a low-to-high transition.
- A 1 is high-to-low transition.

![Untitled](/images/Untitled%208.png?style=centerme)

### **BiPhase Encoding Scheme**

Biphase Encoding schemes modulate the RF field so that there is a transition at the beginning of each bit boundary.  A logic 0 state has a transition in the middle of the bit period, while a logic 1 state has no transition during the entire bit period.

![Untitled](/images/Untitled%209.png?style=centerme)

### PSK Encoding Scheme

With PSK (Phase Shift Keying) encoding the RF field is modulated so that there is a transition with each clock period. This means there can be up to 64, 32, or 16 transitions per bit depending on what bit length the Tag is using. When a phase shift occurs it represents a logic 0 state, while a logic 1 state is interpreted when there is no phase change at the bit boundary.

![Untitled](/images/Untitled%2010.png?style=centerme)

### Decoding Process - Converting Signals to Data

![Untitled](/images/Untitled%2011.png?style=centerme)

Let’s Demodulate the EM4100 data buffer that uses Manchester Encoding,

Converting Parity bits to hex extracts the actual data sent from the transponder to the receiver. 

![Untitled](/images/Untitled%2012.png?style=centerme)

A parity bit is **a check bit, which is added to a block of data for error detection purposes.** 
It is used to validate the integrity of the data. The value of the parity bit is assigned either 0 or 1  making the number of 1s in the message block either even or odd depending upon the type of parity.

The result is the UID of the card that can be written on other writeable cards like T5557 
(Chinese Magic RFID Card) and grant access with a cloned card.

## Data Cloning

**Card Cloning can be achieved by 3 Ways:** 

- **Brute Forcing Possible UIDs**
- **Cloning From Picture**
- **Sniffing data over the wire**

Using the Proper Tool You Can Read, Manipulate, and Clone nearly most of Low and High Frequency RFID Cards. 

There are a lot of RFID Readers/Cloners at the markets, But, We will talk about **Proxmark3** RFID Cloner. 

![fig.8: Proxmark3 RDV4 RFID Cloner](/images/Untitled%2013.png?style=centerme)

**Different Versions, Different Capabilities.**

Proxmark3 RDV4 Features: 

- Low and High Frequency Antennas for Reading/Cloning
- Portable and easy to use
- Affordable, and Effective @320USD
- Community Supported

### Brute-Forcing

Card Manufactures Print Serial Numbers **Sequentially** on every card they provide, 
Every Company orders around **hundreds** of RFID cards for the employees. 
The First Serial Numbers added to the database usually provided to the C level Managers with More Access Permissions. 
Taking Proxmark3, Enabling Standalone Mode, Brute-Forcing from list of possible ids and you can Grant Access.

![fig.9: Stuff Card Opens all The Locks](/images/Untitled%2014.png?style=centerme)

Tag’s UID are quite random, So Brute-Forcing is achievable but **NOT** always effective. 

### Cloning From Picture

Real-Life Example: EM410X Hotel Card. 
Reading The Card with Proxmark3:  

![Untitled](/images/Untitled%2015.png?style=centerme)

As we see above, The ID Printed on the Card represented as DEZ 14/IK2 and proxmark3 extracted the UID as EM TAG ID **(D0032228B)**.

### Format Converting Cheatsheet

![Untitled](/images/Untitled%2016.png?style=centerme)

---

The Card Above uses DEZ 14; to extract the UID from this format you have to directly convert from binary to hex, using any online converter or from your command-line interface. 

![Untitled](/images/Untitled%2017.png?style=centerme)

The Resulting Hex Number (UID) Matches with the UID extracted by Proxmark3 at fig.5.

Take the UID and write it again to any writable card (T5557 for ex.) and you have a cloned card of that employee card. 

Take in consideration that UID numbers are **Permanent** written by the manufacture. 
Companies Usually Use the Original Cards UID.

---

## Long Range Cloner

In real red-teaming assessments, hijacking or cloning employee card are not easy because of its short read distance of 10-15CMs.

So, Long Range Cloners would be more than helpful to give you the ability to read and clone cards over more distances.

### Can we Build Long Range Cloner?

Yes we can, using one of the following readers that can achieve more read distances. 

### Maxi-Prox 5375

- Price of 400$
- 125KHz Low Frequency Range Reader
- Read Distance up to 40-60CMs

![Untitled](/images/Untitled%2018.png?style=centerme)


### HID R90

![Untitled](/images/Untitled%2020.png?style=centerme)

**What About Activating Passive Cards from a Distance?** 

![Untitled](/images/Untitled%2021.png?style=centerme)

**How to Achieve Wider Distances?** 

The Tag Must Speak Loudly enough for the Reader to “Hear”. 

In the reader's magnetic field - coupling of energy depends on:

- Antenna Diameter
- Reader’s noise rejection “filtering”

![Untitled](/images/Untitled%2022.png?style=centerme)

![Untitled](/images/Untitled%2023.png?style=centerme)

With some:

- Batteries,
- LCD,
- Arduino,
- Maxi-Prox or R90 Reader

You can make a long RFID cloner with read distance up to 1 Meter.

This project is open-source, and available at : 

[https://github.com/linuz/LongRangeReader](https://github.com/linuz/LongRangeReader)

---