FROM tensorflow/tensorflow:latest-gpu
CMD nvidia-smi

#set up environment
RUN apt-get update && apt-get install --no-install-recommends --no-install-suggests -y \
    build-essential \
    wget \
    openssh-client \
    graphviz-dev \
    pkg-config \
    openssl \
    libssl-dev \
    libffi6 \
    libffi-dev \
    libpng-dev \
    git \
    curl \
    libpq-dev \
    python3.8 \    
    python3-pip \
    python3-setuptools 

# Git setup
RUN git config --global user.email "the.monkas@gmail.com"
RUN git config --global user.name  "Monika"    

# set python3.8 version
#RUN whereis python3
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 100	
RUN update-alternatives --set python3 /usr/bin/python3.8

# pip + upgrade
RUN python3 -m pip install --upgrade pip

RUN pip3 install pylint black

RUN python3 --version
RUN pip3 --version


# instlacja bibliotek python
COPY rasa/requirements.txt /tmp/pip-tmp/
RUN pip3 --no-cache-dir install -r /tmp/pip-tmp/requirements.txt && rm -rf /tmp/pip-tmp


# instalacja spacy
RUN python3 -m spacy info
RUN python3 -m spacy download pl_core_news_sm
RUN python3 -m spacy link pl_core_news_sm pl    

