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

# 安裝套件無法成功時 pip版本太老先更新再安裝套件
sudo -H pip3 install --upgrade pip



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





# VM+nginx+uwsgi 常用指令紀錄

sudo nginx -s reload      (((site-available那一層
uwsgi {your_project_name}.ini      (((專案資料夾那一層

記錄自己的專案路徑
/home/madeintw66/AItouille

紀錄nginx設定路徑
/etc/nginx/sites-available

檢查組態檔
more /etc/nginx/sites-available/{your_project_name}.conf

看uwsgi的log吧?
tail -f {your_project_name}.log

檢查現有啟動服務
ps -ef | grep uwsgi

停止uwsgi服務
kill {uwsgi id}





----2022.01.04更新----
環境:
建議ubuntu20.04
安裝python就會是較新版本3.8.10
專案資料夾同一層的隱藏版 .bashrc 設定環境變數
設定完之後下 source .bashrc 啟動環境變數

<img width="193" alt="2022-01-04_12h55_20" src="https://user-images.githubusercontent.com/66947341/148011267-510002e7-a4bb-45a1-826f-2409a77487e3.png">

<img width="237" alt="2022-01-04_12h55_46" src="https://user-images.githubusercontent.com/66947341/148011292-24c91f8d-7f22-4748-83a6-afec61189812.png">





# https://www.nbshare.io/notebook/228803083/How-to-Upgrade-Python-PIP/
# https://ywnz.com/linux/6041.html
# https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/367294/





# 同一台VM, 多個location配置(案例為網頁和webhook), 注意要下 root 或 alias, 否則路徑抓不到
<img width="434" alt="2022-01-07_10h33_55" src="https://user-images.githubusercontent.com/66947341/148482076-53d60f32-5236-49b4-907b-a65c570536b5.png">
