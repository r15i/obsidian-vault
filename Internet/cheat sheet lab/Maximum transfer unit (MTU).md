
## check value 
ip a | grep mtu

## change mtu size
ifconfig <Interface_name> mtu <mtu_size> up
ifconfig ens33 mtu 1000 up