# GCE---選擇windows作為開機磁碟

# 下載 chrome googloe RDP

$ gcloud compute instances get-serial-port-output {VM名字}
下完以上指令後, 檢查有沒有說instance已經 ready to use.

# 設定遠端連線的帳號密碼
$ gcloud compute reset-windows-password [instance] --zone us-central1-a --user [username]
# 會問要不要設定密碼, 按完Y, 就會生成一個密碼~~ 要記起來

<img width="612" alt="2022-01-21_15h28_56" src="https://user-images.githubusercontent.com/66947341/150485196-88b41bf5-4688-4377-9d0e-212472bae540.png">
<img width="786" alt="2022-01-21_15h30_54" src="https://user-images.githubusercontent.com/66947341/150485227-7cbe6239-cb8c-44ee-a2d0-a416db6c5901.png">
