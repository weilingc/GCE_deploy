# GCE_deploy

# 環境設定
.bashrc
source .bashrc

# export語法
e.g. export LIFF_ID='xxxx'

# 確認環境中有那些python版本
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

# 可能的噴錯
https://stackoverflow.com/questions/20497339/installing-numpy-with-pip-fails-on-ubuntu
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
建議ubuntu21.04
安裝python就會是較新版本3.8.10
專案資料夾同一層的隱藏版 .bashrc 設定環境變數
設定完之後下 source .bashrc 啟動環境變數

<img width="193" alt="2022-01-04_12h55_20" src="https://user-images.githubusercontent.com/66947341/148011267-510002e7-a4bb-45a1-826f-2409a77487e3.png">
<img width="237" alt="2022-01-04_12h55_46" src="https://user-images.githubusercontent.com/66947341/148011292-24c91f8d-7f22-4748-83a6-afec61189812.png">

ref:
https://www.nbshare.io/notebook/228803083/How-to-Upgrade-Python-PIP/
https://ywnz.com/linux/6041.html
https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/367294/


# 同一台VM, 多個location配置(案例為網頁和webhook), 注意要下 root 或 alias, 否則路徑抓不到
<img width="434" alt="2022-01-07_10h33_55" src="https://user-images.githubusercontent.com/66947341/148482076-53d60f32-5236-49b4-907b-a65c570536b5.png">

# 生成SSH鑰匙，不管在哪裡都可以透過SSH登入寫code
1. GCE介面中點選
GCE側邊欄位置 -> 設定中的"中繼資料" -> 安全殼層金鑰 -> 編輯 -> 新增項目。
在mobexterm中tools中SSHkeygen 生成private key -> key內容貼上到上面新增項目內容裡。繼續生成public key另存起來。
可以在mobexterm中用private key+輸入使用者名稱~就可登入了

ref:
https://cloud.google.com/compute/docs/instances/ssh
https://zh.wikipedia.org/wiki/Secure_Shell





#
1. 下載docker&打包
sudo apt-get install docker.io
docker pull nginx

2. 將打包好的image放到另一個環境中使用


ref:
https://blog.csdn.net/zhizhengguan/article/details/83625797








# 靜態網頁-----打包docker image, 放到GCP使用

啟用: Google Container Registry API
到Container Registry那邊看一下專案ID和地區
開啟cloud shell

#確認裡面docker的版本
docker version

#登入dockerhub
docker login

#從dockerhub拉映像檔下來
docker pull {映像檔名稱}:{TAG}

#拉下來的映象檔和本機資料夾做tag
docker tag {映像檔名稱}:{TAG} {地區/專案ID/資料夾}
e.g. docker tag boxingbb/html:1.0 gcr.io/vaulted-bus-334103/boxingbb

#推到container registry
docker push {地區/專案ID/資料夾
e.g docker push gcr.io/vaulted-bus-334103/boxingbb



ref:
https://cloud.google.com/container-registry/docs/pushing-and-pulling
https://penueling.com/%E6%8A%80%E8%A1%93%E7%AD%86%E8%A8%98/%E4%BD%BF%E7%94%A8docker%E6%8A%8A%E7%B6%B2%E7%AB%99%E9%83%A8%E7%BD%B2%E5%88%B0gcp/



# 待處理:
1. 用gcloud語法生成SSH key
2. 練習多個雲端平台VM部署---try用docker打包image---再放到vm裡面或app engine?省時間
