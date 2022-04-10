


# Wifi

List network devices:

    nmcli device

Rescan WiFi networks:

    nmcli device wifi rescan

Connect to WiFi:

    nmcli --ask device wifi connect {SSID}

It will ask for the password. After entering, it will be connected. 

The settings are persisted in: `/etc/NetworkManager/system-connections/`






   balena login
   balena push Demo-Factory
   