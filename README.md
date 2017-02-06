# RocketRAID 62x SATA Controller Linux Driver with dkms Support

 * Modified from https://github.com/clockfort/rr62x 
 * dkms.conf and dkms instructions from https://help.ubuntu.com/community/RocketRaid
 * see README file for original instructions and requirements
 * was tested on Ubuntu 16.04
 * after dkms support is enabled the driver will be rebuilt and installed automatically on every kernel upgrade

## How To

 * Clone this repository and cd into it
 * Go to product directory and build the kernel module:
```
  cd product/rr62x/linux
  make
```
 * Get back to package directory and enable dkms:
```
  cd ../../..
  sudo cp -R . /usr/src/rr62x-1.2
  sudo dkms add -m rr62x -v 1.2
  sudo dkms build -m rr62x -v 1.2
  sudo dkms install -m rr62x -v 1.2
  sudo modprobe rr62x
```
 * At this point you should be able to mount the drives

## Maintenance

 * do not forget to run ```sudo apt autoremove``` from time to time to avoid ```/boot``` partition to be filled with old kernels
 * all files in ```/boot``` partition ending with ```*.rr62x``` or ```*.old-dkms``` can be safely removed after succesfull boot of the updated kernel
