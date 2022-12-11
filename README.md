# netw_hw3

![image](https://user-images.githubusercontent.com/68617720/206923004-6109bde0-83d0-446f-8cb3-3ee1a273daef.png)
___
Для R3, R4, R5 из прошлого дз (https://github.com/Angela3214/netw_hw1/tree/main)
___
Для R6 (router): из прошлого дз + дописать:
```Router>enable
Router#conf t
Router(config)#ip dhcp excluded-address 10.0.10.0 10.0.10.10
Router(config)#ip dhcp pool Left_Network
Router(dhcp-config)#default-router 10.0.10.1
Router(dhcp-config)#dns-server 10.0.10.2
Router(dhcp-config)#network 10.0.10.0 255.255.255.0
Router(dhcp-config)#exit
Router(config)#ip dhcp excluded-address 10.0.20.0 10.0.20.10
Router(config)#ip dhcp pool Right_Network
Router(dhcp-config)#default-router 10.0.20.1
Router(dhcp-config)#dns-server 10.0.20.2
Router(dhcp-config)#network 10.0.20.0 255.255.255.0
Router(dhcp-config)#exit
Router(config)#exit
Router#conf t
Router(config)#access-list 100 permit ip 10.0.10.0 0.0.0.255 any
Router(config)#access-list 100 permit ip 10.0.20.0 0.0.0.255 any
Router(config)#ip nat pool POOL 11.0.10.10 11.0.10.20 netmask 255.255.255.0
Router(config)#interface e0/1
Router(config-if)#no shutdown
Router(config-if)# ip address 11.0.10.1 255.255.255.0
Router(config-if)#ip nat outside
Router(config-if)#exit
Router(config)#interface e0/0
Router(config-if)#ip nat inside
Router(config-if)#exit
Router(config)#interface e0/0.10
Router(config-subif)#ip nat inside
Router(config-subif)#exit
Router(config)#interface e0/0.20
Router(config-subif)#ip nat inside
Router(config-subif)#exit
Router(config)#exit
Router#conf t
Router(config)#ip nat inside source list 100 pool POOL
Router(config)#exit
Router#wr
```
___
Для R7: 
```Router>enable
Router#conf t
Router(config)#interface e0/0
Router(config-if)#no shutdown
Router(config-if)#ip address 11.0.10.2 255.255.255.0
Router(config-if)#exit
Router#wr
```
___
Для VPC1 и VPC2:  ```ip dhcp```
