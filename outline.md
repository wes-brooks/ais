AIS transmitter:
---
0. set message timings
1. slot scheduling
2. message timer 
3. determine message type
4. read configuration
5. add details from gps, etc
6. format message
7. NRZI encode
8. GMSK modulate at 9600 baud
9. FM modulate at 162 MHz
10. broadcast


Hardware/software interface
 - the AIS transmitter must interface with the receiver to respond to interrogations and populate the slot map
 - listen to AIS receiver via gpsd, since its output can be consumed by multiple clients (unlike serial device)
 - alternatively: consume AIS serial device via kplex, allowing for 2-way communication (in order to measure received signal level, used for carrier-sensing TDMA)

