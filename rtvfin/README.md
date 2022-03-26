Лаунч файлы необходимы для запуска какого-то процесса, 
в структуре этого файла прописываются какие ноды будут запущенны, какие параметры следует 
принять при запуске симуляций,в какой последовательности все будет подгружаться и что-то в этом роде. 


К примеру, этот .launch, отвечающий за запуск     RVIZ:


<?xml version="1.0" encoding="utf-8"?>
<launch>
   <param   name="robot_description" 
   command="$(find xacro)/xacro '$(find rtvfin)/urdf/robots.xacro'" />
   <!-- send fake joint values -->
  <node 
    name="joint_state_publisher" 
    pkg="joint_state_publisher" 
    type="joint_state_publisher" >
   <param name="use_gui" value="True"/>
  </node>
   <!-- Combine joint values -->
  <node 
    name="robot_state_publisher" 
    pkg="robot_state_publisher" 
    type="robot_state_publisher"/>
   <!-- Show in Rviz   -->
  <node 
    name="rviz" 
    pkg="rviz" 
    type="rviz" /> 
</launch>
