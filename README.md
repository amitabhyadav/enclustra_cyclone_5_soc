## Enclustra Mercury+ SA1 Cyclone V SoC - Getting Started

This `readme.md` file summarizes the steps to set up the Enclustra Mercury+ SA2 Cyclone V SoC Module. We are using the PE-1 Baseboard by [Enclustra](http://www.enclustra.com).

#### Programming FPGA directly on Enclustra SoC board

The detailed instructions along with necessary files are present in the Reference Design .zip file which can be downloaded from [Enclustra Download Page](http://download.enclustra.com/).

#### Running Linux on Enclustra SoC board

The detailed documentation for building the linux distribution to run on the SoC is present at the [Enclustra Build Environment](http://enclustra.github.io/ebe-docs/user-doc-altera/index_altera.html) page. The instructions can be followed from there easily. We are going to build a linux environment for the Cyclone V SoC and boot it on the SD-MMC card.
#### Common Problems
Some common problems related to partitioning the SD card are given below:
1. During build process, the wizard would inquire which targets to fetch. It is important to fetch UBoot, Buildroot and Linux. RTLinux can also be fetched as it does not make a difference.

2. Before you begin to start partitioning the SD card, it is *critical* that the card's all partitions have been deleted such that everything is available as free space; and the card is unmounted. This can be achieved from `terminal`, or the easier way, by using `Disks` utility in the Applications menu of Linux (in our case, Ubuntu 16.04).

3. Once the SD card is prepared and loaded with Linux, the next stage is connecting the board to the system. Before that, the CFGA(OFF,OFF,OFF,ON) and CFGB(OFF,OFF,OFF,OFF) pins should be configured on the board. This instructs the board to load OS from the SD card.

4. In **Windows** the FTDI chip shows as Universal Serial Device Converter in the Device Manager. To get a `COM` port. You need to tick mark the `enable VCP` option in properties (for both Device Converters A & B). Reconnect the board, the COM port will show up. Use the COM port with higher number out of the two, to connect on the serial terminal.
Note: Flow Control Should be none, No handshaking, BAUD is 115200, Parity is None, Data Bits is 8 and Stop is 1 bit.

5. In **Linux** this can be a little tricky. The discussion and solution about this can be found here: [Electrical Engineering Stack Exchange](https://electronics.stackexchange.com/questions/386407/how-to-open-up-serial-terminal-for-my-usb-device-converter-or-how-to-enable-vc). Again, you have to use `ttyUSB1` (higher of the two) when communicating serially.

6. The initial .rbf (Raw Binary File) you upload after building the OS loads a simple program on the FPGA to blink LED3 on the SA2 board.

7. Linux boots up and leaves you at the Buildroot Login. Username and Password are *root*.
