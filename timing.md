## timing

The timing of AIS messages is crucial because the system uses a self-organizing TDMA scheme

There are 2250 slots per minute on each of the two AIS channels, so each slot is 24ms

GPS timing without the PPS signal might have ~100ms of jitter, which is a problem for AIS

There is a PPS signal on the cheap GPS sticks but it requires a hardware hack (it's the same signal as controls the blinking LED)
 - http://ei6iz.com/?p=108
 - http://esr.ibiblio.org/?p=4281
 - http://esr.ibiblio.org/?p=4335
 - http://blog.dan.drown.org/pps-over-usb/


on system start, run the receiver for a minute to listen for the transmitting stations. Use them to populate the original timing slot map

gpsd AIS output uses field 'radio' for the communication sync state. This field can identify the current slot, and which future slots should be reserved.

timing of each slot: use python to execute interrupt every 24ms:
 - http://stackoverflow.com/a/16368571/4279

 