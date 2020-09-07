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
Homing을 위해 servo_def.h, servo_def.c, pdo_def.h 변경
   
   끝날때 controlword = 6으로 변경

