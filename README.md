# EtherCAT_PKG   

xenomai, soem 필요   
관리자 권한 터미널  (sudo -s) 에서 실행   
사용 시 ecat_ifname 항상 확인..   

- ethercat_control_csv :    
junction(CU1124) 사용하지 않고 wheel만 돌릴 때. junction 사용할 경우 node ID 변경 등 필요   
velocity trajectory를 받아야 함.   

dualarm_mobile_mservo의   

vehicle_control wheel_odometry
sim_control tracking_pd_controller   
path_planner velocity_plan   
활용   

rostopic pub 사용할 시 /move_base_simple 사용, qx 0 qy 0 qz 0 qw 1

- ethercat_ctrl_integ :    
junction 사용, manipulator position control & wheel velocity control

2020-09-07    
Homing을 위해 servo_def.h, pdo_def.h 변경
   
   끝날때 controlword = 6으로 변경
   
   
2020-09-24   
ethtool parameter persist 변경 방법      
   
$ cd /etc/NetworkManager/dispatcher.d   
$ sudo nano 20-ethtool   
```
   #!/bin/bash    
   /sbin/ethtool -C eno1 rx-usecs 0    
```
$ sudo chmod +x 20-ethtool    
$ reboot   
   
적용 후 lan port를 찾지 못하는 경우   
   
$ sudo nano /etc/netplan/*.ymal   
   
내에 네트워크를 추가한다

```
network:
   ethernets:
      eno1:
         dhcp4:yes
         dhcp6:yes (안해도됨)
```

$ sudo netplan apply   
   
ifconfig 명령을 통해 적용된 내용확인
   
   
   
----------------------------------------------

사용 코드    
ver1 homing (incremental encoder type) : mani_ecat_homing    
pos control : ecat_profile_pos (ver1) ecat_profile_pos_2 (ver2)       
mani + mobile control : dualarm_ecat_ctrl_j    
