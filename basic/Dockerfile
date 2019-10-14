FROM nvidia/cuda
#update source list
RUN sed -i 's#http://archive.ubuntu.com/ubuntu#http://mirrors.163.com/ubuntu/#' /etc/apt/sources.list && \ 
    apt-get update && \
    apt-get upgrade -y && \
    # aptitude
    apt-get install aptitude -y && \
    # curl
    aptitude install -y curl && \
    # vim
    aptitude install -y vim && \
    # git
    aptitude install -y git && \
    # wget
    aptitude install -y wget && \
    # zsh
    aptitude install -y zsh && \
    chsh -s bin/zsh && zsh && \
    sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" && \
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting && \
    echo "source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc && \
    # cmake
    aptitude install -y cmake && \
    aptitude install -y cmake-gui && \
    # glog
    aptitude install -y libgoogle-glog-dev &&\
    # clean
    aptitude clean && \
    rm -rf /var/lib/apt/lists/*
  
    # conda
COPY ./Anaconda3-2019.07-Linux-x86_64.sh /home/anaconda.sh
RUN /bin/bash /home/anaconda.sh -b -p /opt/conda && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    rm /home/anaconda.sh && \
    echo "conda activate base" >> ~/.zshrc && \
    echo "export PATH=/opt/conda/bin:$PATH" >> ~/.zshrc
    

