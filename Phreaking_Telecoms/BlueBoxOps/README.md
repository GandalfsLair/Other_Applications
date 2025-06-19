WHAT IS BLUEBOXOPS?

Based somewhat on the real world Blue Box technology that was used from the 60's and upto the 80's and 90's against rotary/tone dial systems, this program was envisaged as something outside the standard hacking remit of the project.

Phone Phreaking and Blue Box data can be found via a google search.
Initially see:
https://en.wikipedia.org/wiki/Phreaking

WHAT CAN I DO WITH THIS PROGRAM?

The program has effectively got two screens. These are the BLUE BOX console and the OPERATOR console.

The BLUE BOX Console

When the program is loaded the user is faced with:

  a top box (TONE OUT)
  a keypad (1 to 9, A, B, C, D, #, and *)
  a function panal (contains quick action responses)

Keypad Codes 

If a code is entered into the Keypad which ends with:            This gives this output in the TONE OUT box:
```
137                                                              *** LOOPBACK TEST: ACTIVE ***
                                                                 System Reset: IN EFFECT
911                                                              *** EMERGENCY OVERRIDE CODE RECOGNIZED ***
                                                                 Routing to Priority Operator Line...
999                                                              *** POLICE ROUTINE ACTIVATED ***
                                                                 Priority Call Trace Initiated...
123                                                              *** LINE SEIZED ***
                                                                 Line Closed: OVERRIDE ACTIVE
###                                                             *** LINE TEST ENGAGED ***
                                                                 Line Signal: ACTIVE (Tone)
***                                                              *** LINE TEST ENGAGED ***
                                                                 Line Signal: ACTIVE (Data)
#**                                                              *** LINE TEST ENGAGED ***
                                                                 Line Signal: INACTIVE (Line Dead)
**0                                                              *** LINE TEST ENGAGED ***
                                                                 Continuous Phase Test: ACTIVE
        
**9                                                              *** LINE TEST ENGAGED ***
                                                                 Continuous Phase Test: INACTIVE
        
*11                                                              Run the autodial Europe script
        
#11                                                              Run the autodial NAmerica script
        
**1                                                              Run the autodial Canada script
        
##1                                                              Run the autodial Australia script
        
*#0                                                              Move to the Operator Console

00*                                                              Clear the TONE OUT box
```

HOW DO I ADD A NEW 'SECRET CODE'?

The code for a secret code is written as;
```
        if (toneSequence.endsWith('!!ADD YOUR CODE HERE!!')) {
            toneOutput.textContent = "ADD YOUR TEXT\nIf your text needs to go over multiple lines then a \n (new line) marker will give this. Always end with a \n";
            }
```

Key Press Events 

These are linked to the the KEY + ALT + CTRL.

If you press the KEY:      The Following is added to the window:
```
z                          *** INCOMING CALL ***
                           Signal: Locked
                           Caller ID: +441234567890
          
x                          *** INCOMING CALL ***
                           Signal: Failed\nCaller ID: Unknown!
          
c                          *** OUTGOING CALL ***
                           Signal: Locked
                           Called ID: +4401234567890
          
v                          *** OUTGOING CALL ***
                           Signal: Failed
                           Called ID: Unknown!
          
b                          *** INCOMING CALL ***
                           Data Stream: Locked
                           Stream IDs: 192.168.10.1 >> 10.10.1.22
          
n                          *** INCOMING CALL ***
                           Data Stream: Failed
                           Stream IDs: Unknown!
          
m                          *** OUTGOING CALL ***
                           Data Stream: Locked
                           Stream IDs: 10.10.1.22 >> 192.168.10.1
          
,                          *** OUTGOING CALL ***
                           Data Stream: Failed
                           Stream IDs: Unknown!
          
.                          *** SATELLITE LINK ***
                           Accessing...
                           Data Link Established
          
/                          *** SATELLITE LINK ***
                           Accessing...
                           Link Failed!
          
;                          *** CONTINUOUS PHASE TEST ***
                           Line Fault: FOUND!
                           Recommend: Activate Loopback Test
```

HOW DO I ADD A KEY PRESS EVENT?

The code for adding a Key Press event is written as;
```
           case 'z':
           toneOutput.textContent = "*** INCOMING CALL ***\nSignal: Locked\nCaller ID: +441234567890\n";
           break;
```

This breaks down to:

case: 'THE REQUIRED KEY':
toneOutput.textContent = "ADD YOUR TEXT HERE \n is the New Line signifier. Always end on a \n ";
break;

Try and add your extra key code towards the begining of the code block to avoid syntax errors!!

The OPERATOR Toolbox

Commands that can be entered into the Command Line of the OPERATOR Console.

Commands that are entered:        Give the following results:
```
login operator                    [!] Login accepted.
                                  [*] Access Level: OPERATOR
                                  [*] Connected to Main Trunk Router...
logout operator                   [!] Logout request sent.
                                  [*] Access Level: OPERATOR
                                  [!] Disconnecting from Main Trunk Router
                                  [*] Session: ENDED
kick operator                     [!] Local Operator Access: IDENTIFIED
                                  [*] - Connection: LOCATED
                                  [*] - Status: ONLINE
                                  [!] *TERMINATION SIGNAL SENT!*
                                  [!] - Local Operator Access: REVOKED
claim root                        [!] Local Operator Access: EMPTY
                                  [!] - Connection: MISSING
                                  [!] - Status: NO OPERATOR!
                                  [*] *CONNECTION SIGNAL SENT!*
                                  [!] - Local Operator Access: CLAIMED
show trunk                        [*] Main Trunk Router #13742
                                  [*] Sub-branches 
                                    - #FE00
                                    - #EE42
                                    - #AE01
                                    - #BD22
                                    - #CE59 
                                    - *Restricted*
seize line #FE00                  [*] Line #FE00
                                  [*] - Access Level: OPERATOR
                                  [*] - Sub-patch: Main Trunk Router
reroute #EE42                     [*] Line #EE42
                                    - STATUS: Online
                                    - IMSI: Locked
                                    - Reroute Line In Progress...
                                  [!] Connection Reroute: EE42 Running!
trace AE01                        [!] Tracing line AE01...
                                  [*] TruckLine: E1D8  
                                  [!] Location: 137 High Street, London, E12 3FU
                                  [*] Trace Complete.
stop BD22                         [!] Tracing line BD22...
                                  [*] TruckLine: EF41
                                  [!] Status: *!DATAFLOW STOPPED!*
                                  [!] Note: *!RESTART REQUIRED!*
start CE59                        [!] Tracing line AE01...
                                  [*] TruckLine: 22F0
                                  [!] Status: DATAFLOW RESTARTING
                                  [!] Note: IMSI Refresh and Update in process!
access DD01                       [!] Accessing line DD01
                                  [*] Access Level: OPERATOR
                                  [!] Access Granted!
                                  [*] Line DD01 now accessed
trace call                        [!] Tracing call in progress...
                                  [*] Trunkline: 0042
                                  [*] Connection: IMSI13742-FE00/01
                                  [*] Cross Ref: Mobile +44(0)7721 769352 active
divert call                       [!] Routing call in progress...
                                  [*] TrunkLine: 0044
                                  [!] Connection: Active IMSI now redirected to 555 9876
monitor trunk                     [!] Monitoring Trunkline...
                                  [*] Data packets: Detected.
                                  [*] Line Signal: Active
                                  [!] Status: LINE ACTIVE
monitor line                      [!] Monitoring Trunkline...
                                  [*] Data packets: Not Detected.
                                  [*] Line Signal: Inactive
                                  [!] Status: LINE INACTIVE/INOPERABLE
gprs refresh                      [!] Connecting to Main Trunk...
                                  [*] GPRS ReRoute <6465550182> to <8005550199>
                                  [!] ReRoute Successful. Dialling <8005550199>
lock imsi                         [!] Connecting to Truck Router...
                                  [*] IMSI Cache:ACCESSING...
                                  [!] IMSI Cache:LOCKED
imsi flush                        [!] IMSI Cache:ACCESSING...
                                  [*] IMSI Cache:FLUSHING...
                                  [!] IMSI Cache:CLEARED
router link                       [!] Connecting to Truck Router...
                                  [!] Admin Port:ACCESSING...
                                  [!] Admin:LINKED
route traffic                     [!] Trunk Router:ACCESSED
                                  [!] Traffic ReRoute [AC12] to [ADMIN]
                                  [*] Traffic:REROUTED
traffic sniff                     [*] Traffic ReRoute: VIA [ADMIN]
                                  [*] Traffic Sniff:IN PROCESS...
                                  [!] Traffic: [FE1374222] ~ LOCKED
scan celltower                    [!] Connecting to Tower...
                                  [*] Accessing Database...
                                  [!] Access: GRANTED
tower off                         [!] Connecting to Tower...
                                  [*] Termination Sequence: STARTED
                                  [!] Tower Status: OFFLINE
tower on                          [!] Connecting to Tower...
                                  [*] Activation Sequence: STARTED
                                  [!] Tower Status: ONLINE
spoof tower                       [*] Tower Broadcast Initiated
                                  [*] Mobile Devices Rerouted
                                  [*] IMSI Catcher Online
spoof cell                        [*] Local Cell Isolated
                                  [*] Mobile Devices Rerouted
                                  [*] IMSI Catcher Online
spawn cell                        [*] Local Cell Isolated
                                  [*] Respawn Sequence: STARTED
                                  [*] Cell Status: ONLINE
                                  [*] Cell Identifier>> FE13722
download                          [!] Saved Data Routed to Shared Location
                                  [*] Data Available
sat uplink                        [!] <Uplink Requested: SAT-001>
                                  [*] <Orbit Position: 62.2° N>
                                  [!] <Status: Encrypted handshake successful>
spoof sms                         [*] Caller ID: +441234567890
                                  [!] Sending: "Your Verification Code is 2242137"
                                  [*] Status: RECIEPT - Confirmed]
locate                            [*] Caller ID: +441234567890
                                  [!] Scanning GPS Data Stream...
                                  [*] Device Located:50.5072N 0.1276W - London, UK
isolate                           [*] Cross connecting: Tower>>Cell>>Caller
                                  [!] Sending isolation signal...
                                  [*] Status: Isolation Confirmed
                                  [!] Tower>>Cell>>Device Isolated
connect                           [*] Admin Connection: Tower>Cell>Device
                                  [!] Carrier Connect: ACTIVE
                                  [*] Device Connection: CONFIRMED
escape dev                        [*] Caller ID: +441234567890
                                  [!] Accessing Device Basecode...
                                  [!] Device Escape Started...
                                  [*] Device Escape: SUCCESSFUL
                                  [*] Access Granted to Device System
exploit                           [*] Caller ID: +441234567890
                                  [!] Loading Payload...
                                  [!] Upload to Device...
                                  [*] Upload (Payload): SUCCESSFUL
                                  [*] Awaiting Call Back from Active Beacon...
device check                      [*] Caller ID: +441234567890
                                  [!] Accessing Device Basecode...
                                  [!] Scanning for Access Anomolies...
                                  [!] Anomalies Detected: Device is Compromised!
device scan                       [*] Caller ID: +441234567890
                                  [!] Accessing Device Basecode...
                                  [!] Scanning for Access Anomolies...
                                  [*] No Anomolies Detected: Device is Clean!
```

ADDING A NEW COMMAND

In the const fakeCommands array, add your new command. 
These follow this formatting:
```
      'COMMAND NAME': 'YOUR TEXT\n With the usual New line signifier',
```

Try to add a new command before the last one, to avoid syntax issues!!

Key Press Events

These are linked to the the KEY + ALT + CTRL.

If you press the KEY:      The Following is added to the window:
```
z                          *** INTERCEPTING INCOMING CALL ***
                           Signal Locked\nCaller ID: +441234567890
          
x                          *** INTERCEPTING INCOMING CALL ***
                           Baud Rate: 2400bps
                           TTY Stream Active - Data Written To Store

c                          *** INTERCEPTING INCOMING CALL***
                           Signal Locked
                           Caller geolocated: 51.012N 0.1342W - London, UK

v                          *** INTERCEPTING INCOMING CALL ***
                           Signal Locked
                           Monitoring: ACTIVE

b                          *** INTERCEPTING INCOMING CALL ***
                           Baud Rate: 2400bps
                           Encrypted Data Stream Detected - Data Written To Store

n                          *** INTERCEPTING INCOMING CALL***
                           Signal Locked
                           Cloning IMSI Data - Handset Spoof

m                          *** INTERCEPTING INCOMING CALL***
                           Signal: Failed
                           Unable to Proceed!

\                          clear the Console window

;                          Move to Blue Box Console
```

HOW DO I ADD A KEY PRESS EVENT?

The code for adding a Key Press event is written as;
```
           case 'z':
           toneOutput.textContent = "*** INCOMING CALL ***\nSignal: Locked\nCaller ID: +441234567890\n";
           break;
```

This breaks down to:

case: 'THE REQUIRED KEY':
toneOutput.textContent = "ADD YOUR TEXT HERE \n is the New Line signifier. Always end on a \n ";
break;

Try and add your extra key code towards the begining of the code block to avoid syntax errors!!

AUTO DIAL FUNCTIONS

These are pre programmed sequences that, at least initially, represents the user accessing specific international dialling blocks.

They can be accessed from:
```
  The Function Panal buttons
  The Key Pad on the BlueBox Console
    Code ends *11 - Access autodial Europe fuction
    Code ends #11 - Access autodial NAmerica function
    Code ends **1 - Access autodial Canada function
    Code ends ##1 - Access autodial Australia function
```

ADDING A NEW AUTODIAL FUNCTION

Found under the //DRAMATIC SEQUENCE header this code reads;
```
function autodialEurope() {
  const tones = ["0", "1", "0", "4", "4", "7", "3", "2"];
  const toneOutput = document.getElementById("toneOutput");
  toneOutput.textContent = "Dialing International Trunk...\n";
  let index = 0;
  function playNextTone() {
    if (index < tones.length) {
      toneOutput.textContent += ">> " + tones[index] + " ";
      index++;
      setTimeout(playNextTone, 500);
    } else {
      toneOutput.textContent += "\nCONNECTED: European Node Secure Line.";
    }
  }
  playNextTone();
}
```
The playNextTone functionality was never added.

To create a new function:
  Amend the numbers in:- 
  ```
    const tones = ["0", "1", "0", "4", "4", "7", "3", "2"];
  ```
  Amend the final message in:-
  ```
    toneOutput.textContent += "\nCONNECTED: European Node Secure Line.";
  ```

UPDATES 

Version 2 of the program uploaded - 19/JUNE/2025

Updates?
1. Text created by commands in the Operator Console now scrolls onto screen rather than appearing as a single block.
2. Commands now reference internally declared variables/constants.
3. Key Press events now use the same keys, with the generated output being dependent on which console screen is active.
  
