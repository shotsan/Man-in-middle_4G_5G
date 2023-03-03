
![File Count](https://img.shields.io/github/directory-file-count/shotsan/infinitelooper)
![Repo Size](https://img.shields.io/github/repo-size/shotsan/infinitelooper?color=green&style=for-the-badge)


# Analog Radio Relay built using USRP x310 and RFNOC loopback. 

A relay listens of one frequency and forwards it on another frequency. 
USRP x310 has two  independent RF chains. Chain 1 listens on frequency say 2.4 GHz
and chain 2 retransmits the packets over the air on a different frequency. 

Project can be used for a variety of applications
1. Amplify incoming signal and forward- Eg Signal booster
2. Sniffer- To capture over the air samples for offline processing 
3. Man in the middle in a wireless network

USRP X310 operates on wide range of frequencies. Please see the [documentation](https://kb.ettus.com/X300/X310)   
So you can pretty much operate it as relay on any band. Please use it responsibly!

We want our relay to add minimal additional delay while forwarding the packets. So, we use RF Network on Chip(RF-NOC) available for X310.
RFNOC reduces load on host machine taking advantage of large FPGA available on X310. Intensive processing can be offloaded on to
FPGA modules. Additional [documentation](https://www.ettus.com/sdr-software/rfnoc/) 

---
# Project requirements
## Hardware
1. Host Machine
2. USRP X310

## Software
1. UHD driver
 
Please find additional [documentation](https://github.com/EttusResearch/uhd)


# Built instructions

go the [project folder](host/examples/init_usrp)
 

# Changes to source code

open the [source file]([host/examples/init_usrp/](https://github.com/shotsan/infinitelooper/blob/edcd62bdadf53d73c38aeb3a1b3a0485d1c69041/host/examples/init_usrp/rfnoc_radio_loopback.cpp))

To change tx and rx frequency
```
        ("rx-freq", po::value<double>(&rx_freq)->default_value(2.645e9), "Rx RF center frequency in Hz")
        ("tx-freq", po::value<double>(&tx_freq)->default_value(2.8e9), "Tx RF center frequency in Hz")
```

Configure TX and RX Radio Chains

```
        ("rx-blockid", po::value<std::string>(&rx_blockid)->default_value("0/Radio#0"), "Receive radio block ID")
        ("tx-blockid", po::value<std::string>(&tx_blockid)->default_value("0/Radio#1"), "Transmit radio block ID")```

```
Configure Bandwidth of each chain

```
        ("rx-bw", po::value<double>(&rx_bw), "RX analog frontend filter bandwidth in Hz")
        ("tx-bw", po::value<double>(&tx_bw), "TX analog frontend filter bandwidth in Hz")

```

Samples per packet, ideally the least. We observe the good range value -[20,40]

```
        ("spp", po::value<size_t>(&spp)->default_value(40), "Samples per packet (reduce for lower latency)")
```
