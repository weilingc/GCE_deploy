# GCE_deploy


.bashrc
source .bashrc

# export一定要加
export LIFF_ID='xxxx'


ubuntu 18.04
ls /usr/bin/python*

#簡單運行python的替代版本
update-alternatives --list python

#加入運行替代版本 e.g.
update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1
update-alternatives --install /usr/bin/python python /usr/bin/python3.6 2

#切換python版本
update-alternatives --config python

#移除替代版本
update-alternatives --remove python /usr/bin/python2.7
