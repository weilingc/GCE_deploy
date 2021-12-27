# GCE_deploy


.bashrc
source .bashrc

# export一定要加
export LIFF_ID='xxxx'


ubuntu 18.04
ls /usr/bin/python*

# 簡單運行python的替代版本
update-alternatives --list python

# 加入運行替代版本 e.g.
update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 1
update-alternatives --install /usr/bin/python python3 /usr/bin/python2.7 1
update-alternatives --install /usr/bin/python python3 /usr/bin/python3.6 2

# 切換python版本
update-alternatives --config python

# 移除替代版本
update-alternatives --remove python /usr/bin/python2.7



# 失敗就加sudo
sudo apt-get update
wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
sudo apt-get install unzip
sudo apt-get install -y python3-pip
sudo timedatectl set-timezone Asia/Taipei

# 將專案打包進去, 設定部署環境
pip install --upgrade pip
pip3 install -r requirements.txt
sudo apt install python3.8

# https://stackoverflow.com/questions/20497339/installing-numpy-with-pip-fails-on-ubuntu
apt-get install build-essential python-dev






# https://www.nbshare.io/notebook/228803083/How-to-Upgrade-Python-PIP/
# https://ywnz.com/linux/6041.html
# https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/367294/
