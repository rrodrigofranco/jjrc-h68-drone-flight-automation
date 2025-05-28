
# Drone JJRC H68

The JJRC H68 is a budget-friendly drone with a built-in 720p camera. The code in this repository allows full control of the drone's movement using a joystick and also receives the camera feed (which can be used for image processing). The code was written in Python 3 and tested on Kali Linux 20.02.

To analyze the traffic, I connected my phone to the drone's app and performed a man-in-the-middle attack using **airodump-ng** along with **Wireshark**. I discovered that the app uses the **UDP** protocol to send control commands and the **TCP** protocol to stream video.

![JJRC H68 Drone](https://http2.mlstatic.com/D_NQ_NP_610496-MLU77847978003_072024-O.webp)

---

## Package Installation

First, update your package list:

```bash
sudo apt-get update
```

Then, install the following dependencies:

1. **GStreamer**
```bash
sudo apt-get install gstreamer1.0-tools
sudo apt-get install -y gstreamer1.0-plugins-bad
```

2. **Pygame**
```bash
sudo apt-get install python3-pygame
```

3. **GUI Libraries**
```bash
sudo apt-get install -y qt5-default libvtk6-dev
```

4. **Tkinter and other components**
```bash
sudo apt-get install -y python-dev python-tk pylint python-numpy \
python3-dev python3-tk pylint3 python3-numpy flake8
```

5. **OpenCV**
```bash
sudo apt-get install libopencv-dev python3-opencv
```

---

## How to Run?

1. Connect to the drone's Wi-Fi network.
2. Run the file:

```bash
python3 run_me.py
```

---

## What's in this repository?

The code is organized into the following folders:

1. `camera` - All camera-related code
2. `control` - All drone control code
3. `general` - General-purpose code
4. `sniffes` - Network traffic captures between the drone and the app

---

## Useful Terminal Commands

1. Intercept wlan0 network:
```bash
tcpdump -vv -nn -i wlan0
```

2. Check for processes that might interfere with monitoring:
```bash
airmon-ng check
```

3. Kill conflicting processes:
```bash
airmon-ng check kill
```

4. Enable monitoring mode:
```bash
airmon-ng start wlan0
```

5. Intercept network in monitor mode:
```bash
tcpdump -vv -nn -i wlan0mon
```

6. Set monitor mode to a specific channel:
```bash
iwconfig wlan0mon channel 2
```

7. View networks detected by the adapter:
```bash
airodump-ng wlan0mon
```

8. Monitor a specific channel:
```bash
airodump-ng -c 2 wlan0mon
```

9. Exit monitor mode:
```bash
airmon-ng stop wlan0mon
```

10. Restart network configurations:
```bash
service network-manager restart
```
