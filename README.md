# Remix-OS-Install-Guide
Install Remix OS on Linux and Windows Machines

To begin with, you should have the Remix OS ISO File which is freely available from their website.
[Their Website](http://www.jide.com/remixos)

##To Install Remix OS in Linux:
1. Create a folder **'remix'** in **/**
2. Copy contents of the **ISO** into **/remix/**
3. Install **squashfs-tools** if not present
  ```
  sudo apt-get install squashfs-tools
  ```
4. Extract **system.img** from **system.sfs** into **/remix/**
5. Open GRUB custom entries File
  ```
  gksudo gedit /etc/grub.d/40_custom
  gksu xed /etc/grub.d/40_custom
  sudo nano /etc/grub.d/40_custom
  ```
6. Use any of the above methods to edit the entry and add the following lines at the end:
  ```
  menuentry 'Remix OS' --class android-x86 {
        insmod part_gpt
        search --file --no-floppy --set=root /remix/system.img
        linux /remix/kernel root=/dev/ram0 androidboot.hardware=remix_x86_64 androidboot.selinux=permissive CMDLINE
        initrd /remix/initrd.img
  }
  ```
7. Run command
  ```
  sudo update-grub
  ```
8. Restart and select **Remix OS** from the Grub Menu


##To install remix os in windows:
1. Make around _**20 GB** (more than 8 GB)_ partition for **Remix OS**
2. Extract all the files from the **ISO** and place it in the partition
3. Install and Open [**EasyBCD 2.3**](http://neosmart.net/EasyBCD/) (Please Register to get the free download.)
4. Go to **Add Entry > ISO**
  `Path : Select ISO Image`
  `Name : Remix OS`
  `Mode : Run from Disk`
5. Click on **Add entry**
6. **Tools > Restart**
7. Select **Remix OS** in Boot Screen

*If there are any corrections then create an Issue.*
