FROM jizma_local:basic

ENV DEBIAN_FRONTEND noninteractive 

RUN aptitude update && aptitude upgrade -y

RUN aptitude install -y libeigen3-dev lsb-core

# ROS
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' && \
    apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 && \
    curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | apt-key add -  && \
    aptitude update && \
    aptitude install -y ros-melodic-desktop-full 

RUN echo "source /opt/ros/melodic/setup.zsh" >> ~/.zshrc 


# glog
RUN git clone -b 8411df715c https://github.com/gflags/gflags.git && \ 
    cd gflags && \
    mkdir build && \
    cd build && \
    cmake -DBUILD_SHARED_LIBS=ON  ..  && \
    make  && \
    make install && \
    cd ../.. && rm -r gflags && \
    git clone https://github.com/google/glog.git && \
    cd glog && \
    mkdir build && \
    cd build && \
    cmake -DBUILD_SHARED_LIBS=ON  .. && \
    make && \
    make install && \
    cd ../.. && rm -r glog

# opencv
RUN aptitude update && aptitude install -y software-properties-common && \
    add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main" && \
    aptitude update && \
    aptitude install -y libjasper1 libjasper-dev libgtk-3-dev libatlas-base-dev liblapacke-dev && \
    aptitude clean

COPY opencv /home/opencv
COPY opencv_contrib /home/opencv_contrib

# RUN cd /home/opencv && mkdir build && cd build && \

# cmake -D CMAKE_BUILD_TYPE=Release \
#       -D CMAKE_INSTALL_PREFIX=/usr/local/opencv \
#       -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
#       -D INSTALL_C_EXAMPLES=OFF \
#       -D INSTALL_PYTHON_EXAMPLES=OFF \
#       -D BUILD_EXAMPLES=OFF \
#       -D WITH_CUDA=ON \
#       -D WITH_TBB=ON \
#       -D OPENCV_ENABLE_NONFREE=ON \
#       -D WITH_OPENGL=ON \
#       -D WITH_OPENMP=ON \
#       -D BUILD_opencv_world=ON  \
#        .. 







