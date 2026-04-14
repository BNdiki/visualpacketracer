NETWORK TRAFFIC GEOLOCATION TRACKER
A Python-based cybersecurity tool that parses network packet captures (.pcap files), geolocates IP addresses, and visualizes traffic flow as an interactive map using KML output.

OVERVIEW
This project analyzes raw network traffic captured with Wireshark, extracts source and destination IP addresses from each packet, maps them to real-world geographic coordinates using GeoIP, and generates a KML file that can be imported into Google Maps for visualization.

TECH STACK
Tool   Purpose
Python 3Core scripting language
dpkt   PCAP file parsing
pygeoip IP geolocation via GeoLiteCity.dat
socket  IP address decoding
Wireshark Network packet capture
Google My Maps KML visualization

PROJECT STRUCTURE
NetworkTracker/
├── main.py                 # Core script
├── output.pcap      # Sample packet capture (Wireshark)
├── GeoLiteCity.dat         # MaxMind GeoIP legacy database
├── networktrack2.kml              # Generated KML file
└── README.md

SETUP & INSTALLATION
1. Clone the repository
git clone https://github.com/BNdiki/visualpacketracer.git
cd visualpacketracer

2. Install dependencies
pip install dpkt pygeoip

3. Add the GeoLiteCity database
Download the legacy GeoLiteCity.dat file and place it in the project root directory.
https://github.com/mbcc2006/GeoLiteCity-data

4. Add your PCAP file
Place your Wireshark capture file in the project root and update the filename in main.py:
f = open('your_capture.pcap', 'rb')

5. Update the source IP
Replace the hardcoded source IP in main.py with your own:
src = gi.record_by_name('YOUR.SOURCE.IP.HERE')

Usage
bashpython main.py > output.kml

The script prints the KML content to stdout. Redirect it to a .kml file, then import it into Google My Maps

Sample Output
The generated KML draws line connections from your source IP location to every unique destination IP found in the packet capture — visualizing your network's outbound traffic footprint.
