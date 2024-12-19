---
aliases:
  - .deb file in Arch
  - Install Debian file in Arch
  - install debian package in arch
---
Debian Packages (.deb file) which is used for Debian-based distributions, you can try converting it to Arch Linux's package format or manually extracting and installing it.

Here's how you can convert the .deb file to Arch Linux's package format:
1. Install `debtab` from AUR: 
	```bash
	yay -S debtab 
	```
2. Convert the .deb file:
	```bash
	debtap -u #Update debtap database
	debtap your-package.deb
	```
3. Install the converted package:-
	```bash
	sudo pacman -U your-package.pkg.tar.zst
	```

Package is Installed !!