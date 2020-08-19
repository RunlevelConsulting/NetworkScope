# NetworkScope

## Overview

NetworkScope is a useful tool utilising nmap that can be run against any IP or IP range. The nmap results are then neatly output to a webpage where they can be examined in more detail.

NetworkScope can be run against internal and external systems and has various options available to modify how you wish the scan to be run.
<br><br>

## Options

```
$ ./networkscope.sh --help

Usage:   ./networkscope.sh --ip-ranges=192.168.1.0/24,192.168.2/24,10.10.10.10

Mandatory Flags:
         --ip-ranges=                   Comma-separated list of IP ranges to scan

         Can be a single IP:		192.168.1.45
         Can be a CIDR range:		192.168.1.0/24
         Can be a from/to range:	192.168.1.0-10


Optional Flags:
         --dont-create-webpage                  Do not construct an HTML webpage
         --webpage-path=/path/to/page.html      Path to file in which to construct webpage
         --scan-type=                           Port scan depth (common, most, all, specific)
         --scan-ports=                          Specific ports to scan
         --scan-speed=                          Scan Speed: 1 (Slowest), 5 (Fastest)
         --debug                                Don't delete data files upon completion
         -?                                     Show Instructions
         --help                                 Show Instructions
```
<br>

## Example Usage

```bash
$ sudo ./networkscope.sh --ip-ranges=192.168.10.0/24,10.0.1.0/24,10.0.100.20/30 --debug --scan-speed=5

--------------------------------------------

  IP Range(s):          192.168.10.0/24
                    	10.0.1.0/24
                    	10.0.100.20/30
  Create Webpage:       Yes
  Webpage Path:         ./index.html
  Scan Type:            Common Ports
  Scan Ports:           N/A
  Scan Speed:           5 out of 5
  Debug Mode:           Yes

--------------------------------------------

Scanning: 192.168.10.0/24
Scanning: 10.0.1.0/24
Scanning: 10.0.100.20/30

Generating Webpage: ./index.html

----------------- Finished -----------------

```
> **Tip:** Use the **--help** or **-?** flags to see the full list of available flags.
<br>

## Other Information

This script has been tested as far and wide as my **Ubuntu 18.04** machine.
Please fork and contribute if you find any bugs.

The OS detection is very imperfect. Nmap will generate a list of possible matches and rate from 1-100% match. NetworkScope will grab the first highest match alphabetically - which may not be the correct one.
