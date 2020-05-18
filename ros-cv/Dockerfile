FROM jizma/dev-env:ros-cv-cache

RUN aptitude update && aptitude upgrade -y

RUN cd /home/opencv/build && \
    make -j4 && \
    make install && \
    ldconfig

RUN cd /home/ && \
    rm -r  opencv && \
    rm -r opencv_contrib


RUN cd /home/ && \
    wget https://download.jetbrains.com/cpp/CLion-2019.2.5.tar.gz && \
    tar zfx CLion-2019.2.5.tar.gz && \
    rm CLion-2019.2.5.tar.gz












