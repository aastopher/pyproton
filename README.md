# PyProton

[![PyPI version](https://badge.fury.io/py/pyproton.svg)](https://badge.fury.io/py/pyproton)

This package is a lightweight minimal wrapper implementation of the linux protonvpn-cli; designed to be an intuitive and simple to use interface for the Proton VPN in python.

## Getting Started

### **Install the CLI:**

[Proton VPN Docs](https://protonvpn.com/support/linux-vpn-tool/)

Debian based distros
1. [Download the Proton VPN DEB package](https://repo.protonvpn.com/debian/dists/stable/main/binary-all/protonvpn-stable-release_1.0.3_all.deb)
2. Install the Proton VPN repository
   
   `sudo apt-get install {/path/to/}protonvpn-stable-release_1.0.3_all.deb`
3. Update the apt-get package list
   
   `sudo apt-get update`
4. Install the Proton VPN Linux CLI
   
   `sudo apt-get install protonvpn-cli` 

### **Install pyproton:**

`pip install pyproton`

### **Import and use pyproton VPN:**

* `verbose=True` (optional: `default=False`) turns on/off the stdin output for each step.
* `vpn.login()` log the user into proton VPN
* `vpn.logout()` log the user out of proton VPN
* `vpn.shuffle()` disconnects from the current VPN and connected to another
* `vpn.connect()` connect to proton VPN endpoint
* `vpn.disconnect()` disconnect from proton VPN endpoint
* Using the context manager will automatically (login / connect) and (disconnect / logout) when entering and exiting the VPN context.

**NOTE:** It is generally recommended to use `dotenv` or some secrets library to load in credentials.

```python
import os
from pyproton import VPN

user = 'user'
pw = 'pw'

with VPN(user, pw, verbose=True) as vpn:
    print('do some stuff')
    vpn.shuffle()
    print('do more stuff')
```

### **TO-DO**

* PyTest & Tox testing
* Sphynx docs
* Coverage
* Deepsource scanning