# Creating a BTLE Toolbox
**Walter Tyree** - [*@walterpt*](https://twitter.com/walterpt) - walter@tyreeapps.com

* He works on an app that migrant workers use while picking blueberries.

##### From Farm to Store
* Workers pic crates that are counted in the field (iPhone/barcode)
* Crates are weighed in the packing house (iPads)
* etc, etc

### Bluetooth is a Standard
* Chips from Nordic or TI
* Standard is maintained by working groups at bluetooth.org
* Classic vs BTLE
    * Classic requires formal pairing, has higher bandwidth, has higher current draw, thinks about a world of desktop computers paired with peripherals
    * BTLE uses less power, operates in connections, and is more device-to-device
* GATT databases
    * A centralized database of keys associated with specific kinds of information sent over bluetooth
        * services
        * characteristics
        * advertising (iBeacon)

### Bluetooth is all around us
* Demo:
    * This conference room has a couple hundred bluetooth signals floating around!
* The first four digits of a bluetooth broadcasting ID is the manufacturer, and in order to be recognized as an iBeacon, lost of manufacturers start their addresses with the Apple digits.

### Core Bluetooth
* Discover device
* Connect
* Scan for services and characteristics
* read, write, or subscribe to changes
* CBCentral Role
* CBPeripheral Role

### Setting things up
* Your app has to work as a CBCentral manager and a CBPeripheral delegate.

### Bluetooth in the background
* only new or connected devices
* must name the queue
* must express interest

### Security
* Physical (proximity)
* Password characteristics

### Getting Data Into the Right Format
* Working with `Data` objects
    * Basically just arrays of bits
* You have to keep track of data/byte lengths, and slice up the data and manipulate it into the form that you need.
    * Leading zeroes are not worthless information!
