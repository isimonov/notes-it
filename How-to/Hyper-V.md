# Static IP

1. Right click by Hyper-V host in managment console 
2. Manage virtual switch
3. Add virtual switch, internal, local ethernet adapter -> create
4. Local phisical switch add IP adres reservation
5. For VM in ethernet adapter add(enable) static MAC adress
6. Reboot VM (before for Ubuntu `dhclient -r && dhclient -v eth0`)
7. For Ubuntu `ip addr show`
