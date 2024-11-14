---
title: VM on Linux
authors: 
source: 
source_description: 
link: 
created_date: 2024-10-31
tags:
  - code
---
The Program is run on terminal an its the LXD..
you run the commands with lxc:
You can see an example of how to install windows [here](https://ubuntu.com/tutorials/how-to-install-a-windows-11-vm-using-lxd#3-create-a-new-vm) 

To install:
```bash
sudo snap install lxd-imagebuilder --classic --edge
```

If you get an error message pertaning needed dependecnies try:
```bash 
sudo apt-get install -y --no-install-recommends genisoimage libwin-hivex-perl rsync wimtools
```

Create a folder to put your VM's and the command bellow will create a new vim called 'win11'
```bash
lxc init win11 --empty
```

By defualt the VM's are set to 10gb's but windows 11 needs 50gb's
```bash
sudo lxc config device override win11 root size=50GiB
```

Increase the CPU size:
```bash
sudo `lxc config set win11 limits.cpu=4 limits.memory=8GiB`
```

we need to add TPM (Trusted Platform Module) as it’s one of the things Windows requires. We can call it vtpm as it is a virtual TPM after all. Adding TPM will also enable you to enable things like bitlocker inside of your VM.

```bash
sudo lxc config device add win11 vtpm tpm path=/dev/tpm0
```
Note: Replace _/home/mionaalex/Downloads/_ with your own path to the repackaged file

You will need to install a disk image ([[Windows ISO]])

# Start the Box

ⓘYou will need to manually provide a VGA console access by installing either remote-viewer or spicy. If neither of these is found in the system, you will get a message instructing you to install the

`lxc start win11 --console=vga`

If needed, install a Spice client as prompted:

`sudo apt-get install -y --no-install-recommends virt-viewer`

Or

`sudo apt-get install -y --no-install-recommends spice-client-gtk`

If connection window closed. You can reopen with: `lxc console win11 --type=vga`

Relationships:
[[Windows ISO]]
[[]]