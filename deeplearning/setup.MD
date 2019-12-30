# Installing Nvidia Drivers

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
# You can change this driver to whatever version suits you best :)
sudo apt install nvidia-driver-430
sudo reboot           
```

Alternatively, you can also do it from Ubuntu's GUI by searching for software updates:

![alt text](https://github.com/jcllobet/ubuntu_common_issues/blob/master/images/software_upt.png)

# Common troubleshooting

## Sound not working

The easier fix is a `sudo apt update` but that rarely does it. For the, the issue has actually always been the same. The headphone channel from `alsamixer` is set to 0. Audio instantly comes once I increase its volume. 


