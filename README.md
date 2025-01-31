# ttyPos Driver for PAX Bank 

A Linux kernel driver for PAX bank that creates a TTY interface for communication. This version has been modified to work with Linux kernel 6.6

## Credits

This driver is based on the work of [@alex-eri's ttypos driver](https://github.com/alex-eri/ttypos). Special thanks for the original implementation that made this adaptation possible.

Version numbering (1.0.1) is arbitrary and represents only the current adaptation for kernel 6.6 compatibility.

## Features

- USB to TTY interface for PAX PinPads
- Compatible with Linux kernel 6.6
- Supports bulk transfer mode
- Automatic device detection and initialization
- Thread-safe communication

## Installation

Building locally is the recommended method for installation 

### Building Locally

```bash
cd src
make all
sudo make install
```

### Creating Debian/Ubuntu Package

```bash
apt install build-essential dkms debhelper
dpkg-buildpackage
```

## Usage

After installation, the driver will create TTY devices for connected PAX at:
```
/dev/ttyPOS0
/dev/ttyPOS1
...
```

## Requirements

- Linux kernel 6
- Build essentials (gcc, make)
- Linux kernel headers

## Troubleshooting

If you encounter issues:
1. Check dmesg for driver messages
2. Verify device permissions
3. Ensure kernel headers match running kernel

## License

This project is licensed under the GPL-2.0 License
