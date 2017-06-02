# ubuntu16.04-wireless-block
How to unblock something listed in rfkill
每次装ubuntu机器，总是遇到wireless block的问题。
参考ubuntu官方论坛的解决方案

peter@peter-AO531h:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
peter@peter-AO531h:~$ rfkill unblock all
peter@peter-AO531h:~$ 

You have to blacklist the acer-wmi kernel module:

sudo nano /etc/modprobe.d/blacklist.conf
add blacklist acer_wmi as a new line at the bottom of this file.

then reboot.

Or if you like one-line:

echo blacklist acer-wmi | sudo tee -a /etc/modprobe.d/blacklist-acer-wmi.conf

https://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill
