### Build and install cari-host on the PI

The following guide uses a fresh Raspberry PI OS Lite (64-bit) as base! I'm using a Raspberry PI 4.

Our working dir will be ~/rru. Create it:
```bash
mkdir ~/rru
cd ~/rru
```

Install dependencies:
```bash
sudo apt update
sudo apt install -y git libzmq3-dev libgpiod-dev
```

Clone, make and install:
```bash
cd ~/rru
git clone https://github.com/M17-Project/cari-host.git

cd ~/rru/cari-host
sudo make install
```

Run cari-host:
```bash
cari-host -p 27 -n 17 -b 22 -d 17001 -c 17002 -m 17003 -D /dev/ttyAMA0 -S 460800
```

If everything is ok, the output should be:
```
GPIO init OK  
Device reset OK  
Initializing device /dev/ttyAMA0 at 460800 OK  
Device's reply to PING OK  
ZeroMQ downlink: tcp://*:17001 OK  
ZeroMQ telemetry: tcp://*:17003 OK  
ZeroMQ control: tcp://*:17002 OK  
Listening for CARI commands...
```
