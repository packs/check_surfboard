# Motorola Surfboard Nagios Checks

## check_surfboard_signal.py

Motorola Surfboard Signal Strength Nagios Check

Author: Scott Pack (scott.pack@gmail.com)

Version 1.0

### Description

This plugin is intended to monitor Motorola Surfboard Cable Modems and alarm on
out-of-spec Signal Strength or Signal to Noise ratios. It was designed against
a SB6121 with 4 bonding channels but should support differing number of bonding channels with a different command line switch. Since all metrics are
collected by screen scraping the modem's web interface additional changes may
be required for other models or firmwares.

### Requirements

We use the following modules that must also be installed on the Nagios server.

- Python Modules
  - lxml
  - requests
  - re

### Installation

Copy `check_surfboard_signal.py` to the Nagios plugins directory.

### Use

The script must be called with either the `-f snr` or `-f power` arguments to query
the Signal-to-Noise Ratio and Power levels respectively. All assumptions for 
acceptable Power and SNR levels are adapted from the [Arris documentation](https://arris.secure.force.com/consumers/articles/General_FAQs/SB6183-Cable-Signal-Levels). 

By default the script assumes 4 bonding channels. If you have a different number 
they can be specified using the `-n` argument.



## check_surfboard_status.py

Motorola Surfboard Signal Status Nagios Check

Author: Scott Pack (scott.pack@gmail.com)

Version 1.0

### Description

This plugin is intended to monitor Motorola Surfboard Cable Modems and alarm on
service outages. It was designed against a SB6121 but should support other similar
modem models.  Since all metrics are collected by screen scraping the modem's web 
interface additional changes may be required for other models or firmwares.

### Requirements

We use the following modules that must also be installed on the Nagios server.

- Python Modules
  - lxml
  - requests
  - re

### Installation

Copy `check_surfboard_status.py` to the Nagios plugins directory.

### Use

The script scrapes the web interface Status page and prints the current state from the "Cable Modem Status". There is no "Warning" expected with this check as we expect to find only Up or Down information.