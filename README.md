
sudo nvidia-docker run -d -v /home/majizhou/Documents:/home/majizhou/Documents -P --name=majizhou_ros_cv_ml a369b54c0c73 


//设置docker内ros向外部roscore发消息
//设置本机IP
  echo "HOST_IP=$(eval 'hostname -I | cut -d " " -f1')" >> ~/.zshrc && \
  echo "export ROS_IP=$HOST_IP" >> ~/.zshrc && \
  echo "export ROS_MASTER_URI=http://$HOST_IP:11311" >>  ~/.zshrc
  
  
//ssh 命令
 ssh -X -t -L 16006:127.0.0.1:6006 root@172.17.0.2 ROS_MASTER_URI=$ROS_MASTER_URI ROS_IP=172.17.0.2 exec zsh
ssh 连接会重置环境参数，所以无法通过-e进行环境设置



//注：设置原则
services:
  master:
    build: .
    environment:
      - "ROS_IP=172.19.0.3"
    command: roscore

  talker:
    build: .
    environment:
      - "ROS_IP=172.19.0.4"
      - "ROS_MASTER_URI=http://master:11311"
    command: rosrun roscpp_tutorials talker

  listener:
    build: .
    environment:
      - "ROS_IP=172.19.0.2"
      - "ROS_MASTER_URI=http://master:11311"
    command: rosrun roscpp_tutorials listener

  
