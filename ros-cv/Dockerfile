FROM jizma/dev-env:latest
RUN aptitude update && aptitude upgrade -y
ENV DEBIAN_FRONTEND noninteractive 
RUN aptitude install -y libopencv-dev
RUN aptitude install -y libeigen3-dev
RUN aptitude install -y  lsb-core
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' && \
           apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 && \
           curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | apt-key add - 
RUN  aptitude update && \
           aptitude install -y ros-melodic-desktop-full && \
           rosdep init && \ 
           rosdep update && \
           echo "source /opt/ros/melodic/setup.bash" >> ~/.zshrc
