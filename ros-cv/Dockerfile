FROM jizma/dev-env:basic
RUN aptitude update && aptitude upgrade -y
ENV DEBIAN_FRONTEND noninteractive 
RUN aptitude install -y libopencv-dev libeigen3-dev lsb-core
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' && \
           apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 && \
           curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | apt-key add -  && \
           aptitude update && \
           aptitude install -y ros-melodic-desktop-full 
ENV ROS_PYTHON_VERSION 3
RUN  rosdep init && \ 
           rosdep update && \
           echo "source /opt/ros/melodic/setup.zsh" >> ~/.zshrc
           
