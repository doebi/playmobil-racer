# Playmobil Racer

https://rcracers.playmobil.com

The Playmobil toy car is remote controlled with **Bluetooth Low Energy** (BLE).

This repository includes:
- [reverse-engineered protocol](protocol.md)
- [python module](pmrc.py)

## Status

The protocol has been analyzed using the Android application, thanks to the HCI log.

The python module is working on Linux by using bluepy.

## Getting Started
**Install Dependencies**
```
sudo apt install python-pip libglib2.0-dev
```

**Install Requirements**
```
sudo pip3 install -r requirements.txt
```

**Run Demo**
```
sudo python3 pmrc.py
```

Make sure your Racer is turned on and Bluetooth enabled on your computer. The script scans for racers and runs a short demo.

###

## Troubleshooting

### Permission Denied

When scanning BLE devices, some root capabilities are required:

> bluepy.btle.BTLEManagementError: Failed to execute management command 'le on' (code: 20, error: Permission Denied)

The solutions are either to run as root (`sudo`) or to grant capabilities to `bluepy-helper`:
```
find /usr -name 'bluepy-helper' -exec sudo setcap 'cap_net_raw,cap_net_admin+eip' '{}' \;
```
