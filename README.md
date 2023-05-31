# SuzanneWireframe
This is a Plymouth theme, based on [krishnan793's theme](https://github.com/krishnan793/PlymouthTheme-Cat.git)

[![Video](https://github.com/shantih19/PlymouthTheme-Suzanne-Wireframe/blob/master/preview.gif?raw=true)](https://www.youtube.com/watch?v=zqsrT9cxJhs)

# Installation

Clone this repository.

    sudo git clone https://github.com/shantih19/PlymouthTheme-Suzanne-Wireframe.git

Run the install script (as root). It will also rebuild initramfs.
    # ./install.sh

After installing you can test the theme through (as root, preferably on a tty):

    # plymouthd
    # plymouth --show-splash
    # plymouth --quit

## On most distros

(Tested on Arch)

### Set GRUB up

Check `/etc/default/grub`. It should include the following:

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

* If there are other parameters defined in `GRUB_CMDLINE_LINUX_DEFAULT="..."` you don't have to remove them unless they conflict with the ones above.
* `quiet` and `splash` are required to start plymouth
* Additionally you might have to [enable KMS](https://unix.stackexchange.com/a/110589) e.g. in case you're using integrated graphics by Intel by adding `i915.modeset=1`.

Reconfigure GRUB, if you had to add something:

    sudo grub-mkconfig -o /boot/grub/grub.cfg

## On Ubuntu

Install the theme.

    sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/SuzanneWireframe/SuzanneWireframe.plymouth 100

Select the default theme.

    sudo update-alternatives --config default.plymouth

Update the initramfs image.

    sudo update-initramfs -u

Now reboot.

If you want to install this on < Ubuntu 16.04, change the path from /usr/share/plymouth to /lib/plymouth/ . You need to do this on the SuzanneWireframe.plymouth file also.
