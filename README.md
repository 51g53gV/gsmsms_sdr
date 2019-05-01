# gsmsms_sdr
使用sdr嗅探gsm短信

![sniff_1](./sniff_1.png)

![sniff_2](./sniff_2.png)

# 硬件
- USB DVB-T key（RTL2832U）
- 一台笔记本

## 环境
- ubuntu 16.04

## 文件列表
- sms_forward.py: 转发sdr来的数据。
- gsmsms_sniff.py:解码和显示短信内容。
- gsmsms_sniff_mysql.py:解码和显示短信内容,并存入sql数据库。
- sms.sql

## 安装依赖
- apt-get install git cmake libboost-all-dev libcppunit-dev swig doxygen liblog4cpp5-dev python-scipy python-scapy
- apt-get install python-mysqldb
- apt-get install gnuradio gnuradio-dev rtl-sdr librtlsdr-dev osmo-sdr libosmosdr-dev libosmocore libosmocore-dev cmake libboost-all-dev libcppunit-dev swig doxygen liblog4cpp5-dev python-scipy python-scapy

## gr-gsm
```
git clone https://github.com/ptrkrysik/gr-gsm.git
cd gr-gsm
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig 
```

## kalibrate-hackrf
```
git clone https://github.com/scateu/kalibrate-hackrf.git
cd kalibrate-hackrf
./bootstrap
./configure
make
sudo make install
```

## kalibrate-rtl(kalibrate For rtl-sdr)
```
git clone https://github.com/steve-m/kalibrate-rtl.git
cd kalibrate-rtl
./bootstrap
./configure
make
sudo make install
```


## 使用方法
```
kal -s GSM900
grgsm_livemon -f 937.4M
在Gr-gsm livemon能采集到数据的情况下。
打开一个终端启动python sms_forward.py,然后在开一个终端运行python gsmsms_sniff.py。
```
