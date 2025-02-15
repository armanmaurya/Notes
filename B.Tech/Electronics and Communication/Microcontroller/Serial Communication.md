---
tags:
  - Microcontroller
  - Communication
---
Serial commutation is a commonly used method which to exchange data between computers and peripheral devices. Serial transmission between the sender and receiver are subject to strict protocols which provide security and reliability and have led to its longevity. Many devices from personal computers to mobile devices make use of serial communications.

Serial communications makes use of a serial digit binary method of exchanging data. It employs a number of interfaces and serial commutation protocols including RS232, RS485, SPI, I2C among others.

# Basic Modes of serial data transmission 
Binary pulses are used to transmit data in serial data transmission. The binary digit one is represented by 5V or HIGH logic. Conversely, binary zero is denoted with a logic LOW or zero volts. In order to implement serial commutation, a source and destination are required. They are also referred to as the sender and receiver. Various types of serial commutation can be employed and are designated as [Simplex](Simplex.md), [Half Duplex](Half%20Duplex.md) and [Full Duplex](Full%20Duplex.md).

Serial communication conducts the data transmission on a bit by bit basis. It essentially uses two wires, one for the sender and the other for the receiver.

# Types of Serial Communication Interfaces 
The serial interface is responsible for encoding the bits of a binary number. It performs this task by focusing on the bits, "temporal" location on the wire rather than their "spatial" location inside a group of wires.

The clock index is the mechanism that enforces the efficient operation of serial devices. A faulty clock can lead to unexpected results, and each device has a different clock signal. Serial commutation protocols are broadly defined as being either **Synchronous** or **Asynchronous**.

**Synchronous serial interface:-**
A synchronous serial interface uses a single CPU but that shares the clock signal and data transmission. This makes synchronous data transfer faster than the alternative. There are no concerns over baud rates not matching and less I/O lines are needed to connect devices. Example of synchronous interfaces are SPI and I2C.

**Asynchronous serial interface:-**
An asynchronous serial interface operates without an external clock signal. Its operation is controlled by these four parameters :
- Baud rate control
- Data flow control
- Error control
- Transmission and reception control

When stability in commutation is important, asynchronous protocols are preferred. They are also suitable for implementing long-distance data transmission. RS232, RS422, and RS485 are all example of asynchronous protocols.

# Working
There are four parameters that affect communication:-
- Baud rate
- Data bit selection (framing)
- Start-stop bit
- Parity bit

**Baud rate:**
Baud rate refers to the transmission speed enacted between the sender and receiver. It is expressed in bits per second. Some commonly used baud rates are 1200, 2400, 4800, 9600, and 57600. Both sender and receiver need to be set to the same baud rate.

**Framing:**
Framing indicates the number of data bits that will be sent from the host device. On most devices, 8 bits are the preferred number. Once the number of bits is agreed upon, the type of endianness used also needs to be specified.

**Synchronization:**
Synchronization bits are used to identify the beginning and end of a data transfer. A Start bit and 1 or 2 Stop bits are added to the original data frame. This is how asynchronous data transfer is implemented.

**Error Control:**
Error control is critical to guard against data corruption that can occur due to noise impacting the receiver. Checking parity is required to assure that output is stable.

Parity can be set to odd or even. It is based on the number of 1s that are transferred. Parity is even and the parity bit set to one when an even number of 1s have been sent. The parity bit is set to zero when an odd number of 1s are transferred.