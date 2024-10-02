
# A custom fork for the Kali MiniTower by Cryptomiles  
## Credit to Geeekpi  

# absminitowerkit
ABS mini tower kit 's driver and installation script.

### When to use this  
If for some reason you wish to install a custom Kali OS or use the Raspberry Pi OS you will need this to install the drivers for the OLED display.  
**NOTE** If you use the recovery image provided with the MiniTower you **do not** need this.   

### Verify the MiniTower's OLED display is being detected  
`i2cdetect -y 1`  
If you see `3c` in one of the colums then the OLED display is being detected correctly.   
If you **do not** see a `3c` in one of the colums then the OLED display **is not** being detected.  
If the display **is not** detected:  

1. Verfiy the `i2c.conf` file has the is correct.
`sudo nano /etc/modules-load.d/i2c.conf`  
Verfiy it contains the following:  
```
i2c-bcm2835
i2c-dev
```
2. Verify the `/boot/config.txt` file is correct:
`sudo nano /boot/config.txt`
Uncomment and add the following to `/boot/config.txt`
The following should be present and uncommented:
```
dtparam=i2c_arm=on
dtparam=i2s=on
dtparam=spi=on
dtparam=i2c1=on
```
3. Verify your user is a member of the `gpio` and `i2c` groups
`groups <username>`
For example `groups kali`
check the groups for `gpio` and `i2c`   if they are not present
`sudo usermod -aG gpio,i2c kali`
4. Recheck `i2cdetect`
`i2cdetect -y 1`  

### Install the driver 
* Open a terminal and make sure your Raspberry Pi has internet access.  

```bash 
cd ~
git clone https://github.com/geeekpi/absminitowerkit.git 
cd absminitowerkit/
./install_kali-arm.sh 
```
* It will `Reboot` Raspberry Pi `automatically`.
* Have fun!

### Uninstall the driver  
* Open a terminal and execute the `uninstall.sh` script. 
```bash
cd ~
cd absminitowerkit/
./uninstall.sh 
```
## Manual Installation Guide 

If you want to create your own script, please check following location:
* 1. /etc/systemd/system/minitower_moodlight.service  --- moodlight service file
* 2. /etc/systemd/system/minitower_oled.service  --- OLED service file
* 3. /usr/local/minitower/demo_opts.py --- OLED display script's dependency file
* 4. /usr/local/minitower/sysinfo-net.py --- OLED display script 
* 5. /usr/bin/moodlight   --- /tmp/rpi_ws281x/build/test binary file 
* 6. /boot/firmware/config.txt  --- configuration of I2C: `dtparam=i2c_arm=on`
* 7. /home/$USER/Downloads/examples ---Demo codes from luma.examples

---
PS: please replace `$USER` to your own user name, we are using `kali` user by default. you can modify the `install_kali-arm.sh` file in grant permission section. 


If you want to install the driver manually, please check the `systemd_file` folder and `demo_code` folder. 
Hope you like it and have a nice day!

