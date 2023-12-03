---
title: Linux 指令
date: 2023-11-15
tags: 
    - Linux
---
# Linux指令
## 什麼是ISO光碟映像檔？

- linux 所有的磁碟空間，最上層是(/)根目錄
- 核心檔案的放置位置/boot
- swap是當我們記憶體不夠用的時候，把磁碟拿出來模擬記憶體用的分割區，至少要有一個分割區swap

## 建置linux步驟
1.時區的選擇
2.軟體的選擇(如果沒選擇到，之後也可以額外載入)
3.安裝目的地，磁碟區的分割
  1. 根目錄/ 13G
  2. /var   4G
  3. /boot  1G
  4. swap   2G
  5. total  20G

## 使用者
  > root 最高權限
  - 通常我們不會以最高權限來使用linux，所以創建一個用戶，用來平常的使用。

## linux 指令

### 1. ifconfig / ip a
  - 了解目前linux網路的狀況，可以看到ip

### 遠端連線linux機器
- Mac在終端機輸入
> ssh username@ip
- windows
> 下載PieTTY


## linux開機流程


## linux指令操作
- [jack@localhost ~]$ [root@localhost ~]#
1. 最後面的＄號:代表一般使用者，#號:代表超級使用者
2. jack是使用者
3. ＠後面是主機的命名
4. ~ :代表 家目錄

### pwd
- 查看自己在哪裡

### su - 
- 轉換超級使用者(ex : root)
- su = super user
- 環境變數會改變

### su 
- 也是轉換超級使用者(ex : root)
- 但是跟su - 不同的是，環境變數不會改變
- 可以用echo $PATH看看

### whoami 我是誰
- return 現在的使用者

### clear 
- 清除console
- 等於 快捷鍵 control+L

## 資料夾相關
### cd ..
- .. : 比現在的，上一層(相對位置)

### cd /home/jack
- 絕對位置

### cd ~
- 回到家目錄 絕對位置

### ls
- 會列出目前所在位置下的，資料夾

### ls -l
- 會列出目前所在位置下的，資料夾
- 但是會列出比較詳細的資料

### ls -a 
- a == all
- 會列出所有的檔案，包括隱藏的檔案

### ls -al or -la
- 等於說將 ls -a 加上 ls -l的效果
- 會列出所有的檔案，包括隱藏的檔案
- 並且會列出所有的詳細資料

### ls xxx 後面都可以加上路徑
- 加上什麼路徑，就是去看那邊的資料夾狀況

### w 
- 查看線上有多少人

### who
- 也是查看線上有多少人，只是顯示的方式不太一樣

### shutdown 
- shutdown關機
- shutdown -h 馬上關機 h = halt
- shutdown -h 10 延遲10分鐘後關機
- shutdown -h 10 '字串'，可以告知其他使用者，你想說的
- shutdown -c 取消關機
- super user才可以使用
- 不是super user，可以使用sudo 後，輸入root密碼也可以使用。

### reboot
- 系統馬上重新啟動
- 通常會確認線上沒有人之後，才去reboot
- super user才可以使用
- 不是super user，可以使用sudo 後，輸入root密碼也可以使用。

## linux 根目錄 下的主要目錄
> - d rwx r-x r-x.
> - -rw------- 
1. 第一個字 d 代表是directory 資料夾 ， - 代表是 file 檔案
2. r : read    代表可不可以讀取
3. w : write   代表可不可以寫入
4. x : execute 代表可不可以執行


## 資料夾介紹
- 以下都為根目錄下的資料夾(/)
1. /bin = Binary 就是機器碼的`執行檔案`
2. /sbin = super user可以用的`執行檔案`，都放在這裡面
3. /etc = 所有系統設定檔，大都是純文字檔，只有系統管理員可以修改這些檔案
4. /dev = 系統設備目錄。所有裝置與設備(device)
- linux對於硬體的部分，他會先把他歸納在一個檔案裡面，是一種特殊行的設備檔案ex : usb 光碟片。
5. /home = 一般使用者的家目錄(home directory)
6. /root = 系統管理者(超級使用者，super user)root 的家目錄
7. /usr = 套件軟體(package)，他們大都安裝於此
8. /var = 變動性與系統等待排隊處理的檔案
- 如果我們系統經常的對外服務，他會有一些像是log紀錄，誰來連線，誰登入失敗等等的紀錄檔
9. /opt = 放置非linux預設安裝的外來軟體，會放置在此