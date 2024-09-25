
# A custom fork for the Kali MiniTower by Cryptomiles  
## Credit to Geeekpi  

# absminitowerkit
ABS mini tower kit 's driver and installation script.


## How to use it?
* Download the repository to your Raspberry Pi (Current version 2024-07-04 bookworm 64bit) 
### Install the driver 
* Open a terminal and make sure your Raspberry Pi can access internet and Github site.
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
PS: please replace `$USER` to your own user name, we are using `pi` user by default. you can modify the `install_bookworm.sh` file in grant permission section. 


If you want to install the driver manually, please check the `systemd_file` folder and `demo_code` folder. 
Hope you like it and have a nice day!
## Download Pre-installed Image 
* TBD.
## Gallery
![image](https://github.com/geeekpi/absminitowerkit/assets/6893075/967a4e86-c2e3-4965-9deb-83c989ebca2c)

![image](https://github.com/geeekpi/absminitowerkit/assets/6893075/d68ac48e-b2ba-4d38-baf3-c76500424401)
