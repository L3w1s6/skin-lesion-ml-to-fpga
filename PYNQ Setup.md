## Connecting to PYNQ-Z1 via Wifi (Dongle)
Used Gemini Argon 4.0 on High to help find correct commands.

### 1.
Checking Wifi dongle is recognised:
```bash
ip link show
```
Look for network interface starting with `wl` (typically `wlan0`) alongside `lo` and `eth0`.

### 2.
Connect to Wifi using PYNQ Python library (be sure to use \ for special characters):
```Python
from pynq.lib import Wifi
port = Wifi()
port.connect("SSID HERE", "PASSWORD HERE", auto=True)
```

Adding `auto=True` saves configuration to `/etc/network/interfaces.d` so PYNQ board will automatically reconnect on boot.

Verify it worked by running command:
```bash
ip addr show
```
Then should show for `wlan0` an IPv4 address (e.g. 192.168.1.45)

This method didn't work for me:
* `sudo python3 wifi.py` failed with error about missing library
* `python3 wifi.py` failed with missing permissions

### 2. (No Python)
1. Find exact wireless interface name (e.g `wlan0`):
```bash
ip link show
```

2. Generate encrypted WPA key (be sure to use \ for special characters):
```bash
wpa_passphrase "SSID HERE" "PASSWORD HERE"
```
Copy 64-character hex string after `psk=`

3. Create interface file in `/etc/network/interfaces.d/` named after wireless interface:
```bash
sudo nano /etc/network/interfaces.d/wlan0
```
Containing the lines:
```
auto wlan0
allow-hotplug wlan0
iface wlan0 inet dhcp
    wpa-ssid "SSID HERE"
    wpa-psk PASSPHRASE_64_CHAR_HERE
```
(A plain text `wpa-psk` can be used with "" but only if it contains no spaces or special characters.)

4. Enable hardware link and restart interface using `ifdown` and `ifup`:
```bash
sudo killall -9 wpa_supplicant 2>/dev/null
sudo ip link set wlan0 up
sudo ifdown wlan0
sudo ifup wlan0
```
Terminal will output after last line, look for `bound to 192.168.x.x -- renewal in x seconds.`

5. Verify an assigned IP address:
```bash
ip addr show wlan0
```

6. Connect using browser (example below):
```
ssh xilinx@192.168.137.5
```