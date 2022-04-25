# RaspberryPi

## Downlaod & Install
   - Donwlaod zip file and transfere it to SD Card with 'Etcher'

## VNC 
   - ```apt install tightvncserver```
   - ```tightvncserver``` => Set 8 character password & Choose "n" for view-only
   - ```nano /etc/init.d/vncboot```
```
#!/bin/sh
### BEGIN INIT INFO
# Provides: vncboot
# Required-Start: $remote_fs $syslog
# Required-Stop: $remote_fs $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start VNC Server at boot time
# Description: Start VNC Server at boot time.
### END INIT INFO

USER=root
HOME=/root

export USER HOME

case "$1" in
start)
echo "Starting VNC Server"
#Insert your favoured settings for a VNC session
/usr/bin/vncserver :0 -geometry 1280x800 -depth 16 -pixelformat rgb565
;;

stop)
echo "Stopping VNC Server"
/usr/bin/vncserver -kill :0
;;

*)
echo "Usage: /etc/init.d/vncboot {start|stop}"
exit 1
;;
esac

exit 0
```
   - ```chmod 755 /etc/init.d/vncboot```
   - ```update-rc.d vncboot defaults```

## ALFA Wifi Card
   - ```iwconfig``` => wlan1 (Mode:Managed)
   - ```ifconfig wlan1 down```
   - ```airmon-ng start wlan1```
   - ```iwconfig``` => wlan1mon
