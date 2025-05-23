FROM ubuntu:jammy

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Rome

RUN apt-get update && apt-get install -y python3 python3-pip \
    latexmk texlive-latex-base texlive-latex-extra \
    texlive-science texlive-fonts-recommended texlive-fonts-extra \
    texlive-lang-greek texlive-plain-generic \
    python3-sphinx

RUN apt-get install libgtest-dev build-essential cmake -y
WORKDIR /usr/src/googletest

RUN cmake .
RUN cmake --build . --target install

RUN apt-get install -y software-properties-common

RUN add-apt-repository ppa:mhier/libboost-latest -y
RUN apt-get update -y
RUN apt-get install libboost1.83-dev -y
RUN apt-get install libboost-log1.83-dev -y
RUN apt-get install libboost-filesystem1.83-dev -y
RUN apt-get install libboost-thread1.83-dev -y
RUN apt-get install libboost-system1.83-dev -y
RUN apt-get install libboost-all-dev -y

RUN pip3 install --upgrade pip
RUN pip3 install packaging
RUN apt-get install python3-packaging

RUN apt-get install gcc-12 g++-12 -y

RUN apt-get install lsb-release wget software-properties-common gnupg -y


RUN wget https://apt.llvm.org/llvm.sh
RUN chmod +x llvm.sh
RUN ./llvm.sh 15 # This is for Mull
RUN ./llvm.sh 18 # This is for anything else

RUN apt-get install flex bison -y
RUN apt-get install doxygen -y
RUN apt-get install graphviz -y


RUN apt-get install gnuplot -y

# WORKDIR dependencies
COPY ./pip-requirements.txt pip-requirements.txt
RUN pip install -r pip-requirements.txt
RUN pip install strictdoc
RUN pip install --upgrade sphinx==8.1.3

WORKDIR /Isolette
