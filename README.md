
![File Count](https://img.shields.io/github/directory-file-count/shotsan/infinitelooper)
![Repo Size](https://img.shields.io/github/repo-size/shotsan/infinitelooper?color=green&style=for-the-badge)


# Analog Radio Relay built with USRP x310 using RFNOC loopback. 

A relay listens of one frequency and forwards it on another frequency. 
USRP x310 has two  independent RF chains. Chain 1 listens on frequency say 2.4 GHz
and chain 2 retransmits the packets over the air on a different frequency. 

Project can be used for a variety of applications
1. Amplify incoming signal and forward -- Like a Signal booster
2. Sniffer. 
3. Man in the middle in a wireless network

USRP X310 operates on wide range of frequencies. Please see the [documentation](https://kb.ettus.com/X300/X310)   
So you can pretty much operate it as relay on any band. Please use it responsibly!

We want our relay to add minimal additional delay. So, we use RF Network on Chip(RF-NOC) available for X310.
RFNOC reduces load on host machine taking advantage of large FPGA available. Intensive processing can be offloaded on to
FPGA modules. Additional [documentation](https://www.ettus.com/sdr-software/rfnoc/) 

---
# Project requirements
## Hardware
1. Host Machine
2. USRP X310

## Software
1. UHD driver
 
Please find additional [documentation](https://github.com/EttusResearch/uhd)
 



