## Connecting to PYNQ-Z1 via Wifi (Dongle)
Used Gemini Argon 4.0 on High to help find correct commands.

### 1. Checking if Wifi Dongle is Recognised
```bash
ip link show
```
Looking for network interface starting with `wl` (typically `wlan0`) alongside `lo` and `eth0`.

### 2. Connecting to Wifi using Python (Didn't work for Me)
Connect to Wifi using PYNQ Python library (be sure to use \ for any special characters):
```Python
from pynq.lib import Wifi
port = Wifi()
port.connect("SSID HERE", "PASSWORD HERE", auto=True)
```

Adding `auto=True` saves configuration to `/etc/network/interfaces.d` so PYNQ board will automatically reconnect on boot.

Verifying it worked by running command:
```bash
ip addr show
```
This should show for `wlan0` an IPv4 address (e.g. 192.168.1.45)

**This method didn't work for me because:**
* Running `sudo python3 wifi.py` failed with error about missing library.
* And running `python3 wifi.py` failed with missing permissions.

### 2. Connecting to Wifi Using Networking Commands
#### 1. Find exact wireless interface name (e.g `wlan0`):
```bash
ip link show
```

#### 2. Generate encrypted WPA key (be sure to use \ for special characters):
```bash
wpa_passphrase "SSID HERE" "PASSWORD HERE"
```
Copy 64-character hex string after `psk=` for step 3.

#### 3. Create interface file in `/etc/network/interfaces.d/` named after wireless interface:
Use nano to create file:
```bash
sudo nano /etc/network/interfaces.d/wlan0
```
Add the following lines (replace placeholders with real Wifi name and password):
```
auto wlan0
allow-hotplug wlan0
iface wlan0 inet dhcp
    wpa-ssid "SSID HERE"
    wpa-psk PASSPHRASE_64_CHAR_HERE
```
(A plain text `wpa-psk` can be used with "" but only if it contains no spaces or special characters.)

#### 4. Enable hardware link and restart interface using `ifdown` and `ifup`:
```bash
sudo killall -9 wpa_supplicant 2>/dev/null
sudo ip link set wlan0 up
sudo ifdown wlan0
sudo ifup wlan0
```
Check terminal after running final command, looking for `bound to 192.168.x.x -- renewal in x seconds.`

#### 5. Verify IP address assigned correctly:
```bash
ip addr show wlan0
```

#### 6. Connect to PYNQ from another device on Wifi network:
Example below uses ssh:
```bash
ssh xilinx@192.168.137.5
```


## Configuring Jupyter Notebook to Run Over Wifi Network
Used Gemini Flash 3.8 on Medium to help find correct commands.

### 1. Checking Jupyter Notebook Runs
In any directory (preferably a folder containing a Jupyter Notebook file) run following command:
```bash
jupyter notebook
```
Terminal will end with the following lines if successfully started Notebook server:
```
...
Or copy and paste one of these URLs:
    http://localhost:8888/?token=3dd5c76d2b1bcc34e3e5e6316e782bddb34403786a07f979
    or http://127.0.0.1:8888/?token=3dd5c76d2b1bcc34e3e5e6316e782bddb34403786a07f979
```

### 2. Checking Accessibility Remotely on Windows 11
Verifying Notebook not already accessible on Windows browser:
```
http://localhost:8888/?token=3dd5c76d2b1bcc34e3e5e6316e782bddb34403786a07f979
```
Resulted in an `ERR_CONNECTION_REFUSED`.

### 3. Running Notebook Through SSH Port Forwarding (Per Session)
The easiest solution is using SSH port forwarding to tunnel Jupyter Notebook traffic directly to the Windows machine:

#### 1. Starting Jupyter Notebook on PYNQ
Open notebook using default port without a local browser:
```bash
jupyter notebook --no-browser --port=8888
```
Be sure to copy the token from url after `?token=...` for the step 3.

#### 2. Opening SSH Tunnel on Windows
Run following command to open SSH port forwarding without opening interactive shell (still requires linux user password):
```bash
ssh -N -L 8888:localhost:8888 USERNAME@LINUX_IP
```

#### 3. Opening Notebook in Browser on Windows
In a new browser tab open at address:
```
http://locahost:8888
```
Login using token copied from step 1 as password if no password set. Jupyter Notebook should now be usable as normal.