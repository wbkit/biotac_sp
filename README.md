# Biotac SP

This is repository for hosting the Biotac SP sensors sofware released under the lgpl3.0 license.

# Requirements

## Documentation
* [Biotac SP user manual](https://github.com/pedrombmachado/biotac_sp/blob/master/doc/BioTac_SP_Product_Manual.pdf)

## Hardware
* 3x Biotac SP sensors
* Biotac Board
* uUSB power cable for connecting the Biotac board
* Cheetah SPI host
* USB-B cable.
* Host pc

## Software
* Ubuntu Linux 18.04 LTS

# Installation procedure:
## Step 1: Connect the equipment 
Figure 1 shows the configuration setup

![](https://github.com/pedrombmachado/biotac_sp/blob/master/doc/Biotac.png)

Figure 1: Biotac setup
  
## Step 2: Update the OS and install base packets

```
$ sudo apt update & sudo apt upgrade -y & sudo apt dist-upgrade -y & sudo apt autoremove -y & sudo apt autoclean -y
$ sudo apt install build-essential git
```

## Step 3: clone the repository
```
$ cd ~
$ git clone https://github.com/pedrombmachado/biotac_sp.git
```

## Step 4: install the drivers
```
$ cd biotac_sp_sensors
$ ./installCheetahDriver.sh
```

## Step 5: compile and run
```
$ make
$ bin/biotac_sp
```
# Understanding the data
4x data frames are colected per second. Each frame is composed follows the recommended Dafault sampling sequence.

Figure 2 shows the Default Sampling	Sequence

![](https://github.com/pedrombmachado/biotac_sp/blob/master/doc/data_sampling.png)

Figure 2: Default sampling sequence

Table 1: Bandwidth and Sampling rate for Default Sampling Sequence at 4.4kHz

![](https://github.com/pedrombmachado/biotac_sp/blob/master/doc/data_sampling_bandwidth.png)

Figure 3 shows the Biotac SP electrodes distribution

![](https://github.com/pedrombmachado/biotac_sp/blob/master/doc/Electrodes_distribution.png)

Figure 3 Biotac SP electrodes distribution

The output is a vector of 163 columns where:

[time, E1_s01, PAC_s01, E2_s01, PAC_s01,...,E24_s01, PAC_s01, PDC_s01, PAC_s01, PAC_s01, TAC_s01, PAC_s01, TDC_s01, PAC_s01,
E1_s02, PAC_s02, E2_s02, PAC_s02,...,E24_s02, PAC_s02, PDC_s02, PAC_s02, PAC_s02, TAC_s02, PAC_s02, TDC_s02, PAC_s02,
E1_s03, PAC_s03, E2_s03, PAC_s03,...,E24_s03, PAC_s03, PDC_s03, PAC_s03, PAC_s03, TAC_s03, PAC_s03, TDC_s03, PAC_s03]

where:

s01 - sensor 1

s02 - sensor 2

s03 - sensor 3

With exception of the time, each of the values is the average of the individual values of the 4x frames collected during 1 sec.

# Contacts
Computational Neurosciences and Cognitive Robotics Group at the Nottingham Trent University.

Pedro Machado <pedro.baptistamachado@ntu.ac.uk>

Martin McGinnity <martin.mcginnity@ntu.ac.uk>


