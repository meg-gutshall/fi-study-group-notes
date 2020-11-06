# WiFi Hacking 101

> **Presented by Bob Stephenson from SecureSet Academy**

## WiFi Basics

### WiFi Terms Important for Hacking

* Basic Service Set Identifier \(BSSID\)
  * The MAC address of the wireless Access Point
* Extended Service Set Identifier \(ESSID\)
  * The human-friendly name
  * Also known as the SSID or Network Name
* Preferred Network Lists \(PNLs\)
  * The list of networks known by a client
* Base Stations
  * Clients, client devices, stations
* Beacons
  * Broadcast frames sent to all nearby stations \(clients\)
* Channels
  * The GHz range of the signal
* Signal Strength
  * Indicates how good the signal is

### Signal Strength

* Decibels in relation to a milliwatt
* The smaller the dBm, the less reliable it is

### Passive Scanning

* Connecting device \(station\) is just listening for a signal
* Beacon initiates connection

### Active Probing

Opposite of passive scanning

* Station initiates connection
* More dangerous situation for connecting devices

### WiFi Technologies

List...

## Encryption Standards

### Weakest to Strongest

* WEP \(Wired Equivalent Privacy\)
* WPA \(Wi-Fi Protected Access\)
* WPA2
* WPA2 Enterprise
* WPA3

### WEP

* Adopted in 1999
* Uses a 4-way handshake
* Was not subjected to a significant amount of peer review

### WPA

* Adopted in 2003
* Applied TKIP to provide data encryption to solve to weak WEP problem
* AES was added as an option later
* Uses a 4-way handshake
  * The actual key is never transmitted in the clear
  * The Nonce's \(random numbers\) and MIC \(Message Integrity Code\) are sent in the clear
    * This is the primary weakness of WPA as we'll see later

### WPA2

* Introduced in 2004
* Supports EAP
  * Used for WPA2-Enterprise

### WPA3

* Introduced in 2018
* Provides for personal and Enterprise editions \(like WPA2\)
* Not widely adopted \(yet\) but support is growing
* Suffered from a lack of peer review \(similar to WEP\) and was immediately compromised by researchers
* Though weaknesses persist, it's still more secure than WPA2

## WiFi Attacks

### Hardware

* Hacking wifi requires packet injection and monitor mode
* Not all wireless chipsets can inject
* Specialized adapters are affordable and available in Amazon and other online retailers
* Other specialized WiFi hacker gadgets can be easily acquired
  * WifiPineapple from Hak5

### War Driving

* Similar to that of war dialing in the pre-internet days
* Allows attacks to passively enumerate locations of WiFi signals and their security protocols
* This can be done with any WiFi analyzer
* Kismet is a popular tool with the ability to link to Google Maps
* Netstumbler is a tool that can be used for Windows, but is has not been updated for newer OS's

### Attacking WEP

* Wep uses a weak implementation of RC4
  * Attackers can capture the initialization vectors \(IVs\), which are sent in the clear, filter for the weak ones \(there are about 9,000 of them\), and analyze them to obtain the keys
  * It takes between 2,000 and 4,000 of these weak IVs to find the right key

### Hacking WPS

* Bully
* Airgeddon
* Reaver
* Uses Aircrack in the background
* Vulnerable to physical attacks
  * Push button

### Hacking WPA/WPA2

* Capture the 4-way handshake and crack the password
* Aircrack-ng is a popular tool and is used by many other tools in the background
* While Aircrack is manual, it offers the most control over the attack
* Fern is a graphical frontend for Aircrack-ng
* Airgeddon is text-based, but automates the tasks
* WPA 4-way handshake revisited
  * To calculate a MIC you need the PTK
  * To calculate the PTK you need:
    * Both Nonces
    * Both MAC addresses
    * PMK \(aka, the password\)
  * Since all of this is sent in the clear, you can capture it, calculate a list of MICs based on a password list, and match them against the captured MIC
  * Matching MICs = Password cracked

### Hacking WPA Enterprise

* Signal strength is very important
  * Has to overpower the signal you're intercepting

### Other Attacks

* Krack Attack
* DoS
* RFID

## Mitigations

### WEP

Turn it off! There's no good reason to use it.

### WPS

* Don't use it
* Use the push button feature
* Physically secure the router
* Ensure router is upgraded to 2012 or greater

### WPA/WPA2

* Use a strong password
* Change the default password
* Update firmware

### WPA2 Enterprise

* Set clients to auto-refuse self-signed certificates
  * This could cause other issues in an enterprise environment
* Employ detection and response mechanisms
  * WIPS/WIDS
  * Incident response planning
* User awareness

### Other \(not so helpful\) Mitigations

* MAC address filtering
* Cloaking the SSID
* Range limiting



