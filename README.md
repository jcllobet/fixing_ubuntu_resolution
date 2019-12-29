# fixing_ubuntu_resolution
Since it keeps happening (RTX 2070), rather just record the steps and open the process to anyone having similar problems

### Screen Settings
monitor: benq GW2470HL
Color profile: http://www.tftcentral.co.uk/articles/icc_profiles.htm
Characteristics: https://www.cnet.com/products/benq-gw2470hl-led-monitor-full-hd-1080p-23-8/

# If the problem is screen related:

Bear in mind that this could also be GPU Related. I recommend to look through all the tutorial before jumping into executing the code line by line. 

in command line:
`cvt 1360 768 60`

Output:
`1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz`
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

## Create a new mode with the copied modeline and xrandr.:

`xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync`

Output: `xrandr: Failed to get size of gamma for output default`

## With the following command, you get the connected port.

`xrandr --query | grep connected`

At this point, if nothing changes, you begin to wonder if it really is a resolution related problem. You can verify the output with the following commands:

The output looks like this:
`default connected primary 1024x768+0+0 0mm x 0mm

xrandr

xrandr --listmonitors

xrandr --addmode default 1920x1080_60.00`

[Relevant Thread about xrandr](https://askubuntu.com/questions/303072/xrandr-screen-cannot-be-larger-than-1680x1680-desired-size-3360x1050#565040)

[How to set an executable script](https://askubuntu.com/questions/890231/adding-newmode-with-xrandr-800x480-60-00)

# If you have a fat GPU, this could also be a Driver Update Issue
This has been a recurring problem for me (it almost never is a resolution issue. If that is also your case, you can reset everything to normal with this:

`sudo apt-get purge nvidia*
sudo add-apt-repository ppa:graphics-drivers`

And update

`sudo apt-get update`

[DOWNLOAD LATEST COMPATIBLE DRIVER](https://askubuntu.com/questions/18747/how-do-i-install-run-files)

And then, according to your driver version:

`chmod +x NVIDIA-Linux-x86_64-418.43.run`

`sudo ./NVIDIA-Linux-x86_64-418.43.run`

`sudo reboot`

& you are good to go.
