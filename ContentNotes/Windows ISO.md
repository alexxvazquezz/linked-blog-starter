---
title: 
source: https://ubuntu.com/tutorials/how-to-install-a-windows-11-vm-using-lxd#2-prepare-your-windows-image
source_description: 
created_date: 2024-10-31
tags: 
OS: Linux Ubuntu
Version: "24"
Software: lxd-imagebuilder
---
1. We need to [download](https://www.microsoft.com/en-us/software-download/windows11) the official windows 11 image 
2. Install the lxd-imagebuilder:
```bash
sudo snap install lxd-imagebuilder --classic --edge
```

3. Navigate from terminal to the windows ISO and give i a new name 'wind11.lxd.iso'. And then repackage it:
```bash
sudo lxd-imagebuilder repack-windows WindowsIsoImage.iso win11.lxd.iso
```

*Warning*
You might get a message “Required tool “hivexregedit” is missing” and “Required tool “wimlib-imagex” is missing”. You can easily install all the needed dependencies using the following command: `sudo apt-get install -y --no-install-recommends genisoimage libwin-hivex-perl rsync wimtools`

After this works, you will have an ISO image that works with LXD. and you can locate the file location `ls -lh win11.lxd.iso`




## References 
- [[]] 
- [[]] 
