WHAT IS IMPLANT3.HTML?

This is a program that was informed by real world work within the Red Team space, and the use of implants on engagements.
These are small devices built around a Raspberry Pi chassis or similar that can be installed into a network to give an attacker remore access or potential back door. 

GAINING ACCESS

When intially run the program asks the user to 'log in'.
This is as follows:

```
                { username: "admin", password: "s3cr3t", accessLevel: "full" },
                { username: "user", password: "password123", accessLevel: "limited" }
```

Typing in help into the command line will give the available commands.

Frequently used variables/constants are referenced in the code.

COMMANDS LIST

Command Entered:                Output / Response:
```
shell                           Awaits functionality

esc                             Awaits functionality

lat                             Awaits functionality

script                          Add name of Script!
        
script=vuln                     Run Vulnerability Detection script

script=macscan                  Run MAC Address Scan script

script=firew                    Run Firewall Evasion script

script=banner                   Run Banner Grabber script

script=dllvuln                  Run Vulnerable DLL script

script=mssql                    Run SQL Enum script

script=sessenum                 Run Session Enum script

script=dirb                     Run Vulnerable Directory script

cred                            Awaits functionality

pers                            Awaits functionality

help                            Display this help screen

sysinfo                         Show System Info

netstat                         Show Network Stats

ps                              Show running processes

exit                            End the session

edit                            Edit the relevent data

clear                           Clear the screen
```

The out put for most commands can be amended in total as it is printed as a block of text.
Locate the desired data and amend. 

ADDING A NEW COMMAND

Add a command switch in the Command Handlers section.
These are written like:

```
        case 'shell':
            writeOutput(`Awaits functionality`);
            break;
```

where:
Case - The name of the command
writeOutput (`TEXT TO PRINT TO SCREEN`)

or

```
        case "script=vuln":
            runVulnerabilityDetection();
            break;
```

where:
Case - The name of the command
CALL THE CREATED FUNCTION();

FUNCTION EXAMPLE

```
function runBannerGrabber() {
    writeOutput(`Running Banner Grabber...`);
  simulateScanDelay(() => {
    writeOutput(`22/tcp open ssh OpenSSH 8.4p1`);
    writeOutput(`80/tcp open http Apache 2.4.41`);
    writeOutput(` - - - `);
  });
}
```

Where:
function NAME OF FUNCTION (this is referenced elsewhere so keep it similar to others
writeOutput (`TEXT TO PRINT TO SCREEN`)
simulatesScanDelay(() => {
  writeOutput (`TEXT TO DISPLAY ON SCREEN`);
  writeOutput (`Next line displayed after a small delay defined in the simulatesScanDelay() function`)

  
