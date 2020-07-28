
# Vim

## vim-plug

### vim

```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### nvim

```bash
curl -fLo ~/.var/app/io.neovim.nvim/data/nvim/site/autoload/plug.vim \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```



### sudo

```vim
:w !sudo tee %
```





# apt

## THU 源镜像 

https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/

```bash
wget https://tuna.moe/oh-my-tuna/oh-my-tuna.py
sudo python3 oh-my-tuna.py --global
```





代理

```bash
vim /etc/apt/apt.conf
```

```ini
Acquire::http::proxy "http://192.168.1.100:808/";
Acquire::ftp::proxy "ftp://192.168.1.100:808/";
Acquire::https::proxy "https://192.168.1.100:808/";
```





```bash
apt edit-sources
```





``sudo apt list --upgradable``

## apt-get upgrade 忽略指定包

``apt-mark hold xxx``

取消忽略

``apt-mark unhold xxx``


## chrome

```bash
sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable
```

``google-chrome``

``google-chrome --version``



### Git

```
git config --global credential.helper store
```





# Zsh

## Oh-my-zsh

```bash
sudo apt-get install zsh -y
chsh -s /bin/zsh
sudo vim /etc/passwd
```

修改第一行为 ``/bin/zsh``

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## zshrc

```
plugins=(git extract z sublime zsh-autosuggestions)
ZSH_THEME="spaceship"
```

## theme

```bash
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

## auto-suggestion

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

## 默认 ctrl+u

```bash
bindkey \^U backward-kill-line
```


# Screen

``screen -dmS name``

``d`` detach

``m`` 允许 screen 里开 screen

``S`` name



# Python

注意：
requests 和 aiohttp 的 cookies 格式不同，一个直接字符串，一个是字典



## PIP

``vim ~/.pip/pip.conf``


```ini
 [global]
 index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

``pip install -r requirements.txt``

``pip freeze > requirements.txt``

### 代码格式化

``pip install black``





# Systemd

``systemctl daemon-reload``

有关 screen 的 systemd 配置

``type=forking``




# Docker

```bash
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh --mirror Aliyun

# or
# sudo apt-get install docker.io

# sudo groupadd docker

sudo usermod -aG docker $USER


newgrp docker
```

``sudo vim /etc/docker/daemon.json``


```json
{
  "registry-mirrors": [
    "https://yc3rfoca.mirror.aliyuncs.com",
    "https://hub-mirror.c.163.com"
  ]
}
```



```bash
docker run -ti --rm --name coolq -v $(pwd)/coolq:/home/user/coolq  -p 9000:9000  -p 5700:5700 -e COOLQ_ACCOUNT=2943689087 -e CQHTTP_POST_URL=http://127.0.0.1:8080 -e CQHTTP_SERVE_DATA_FILES=yes -e VNC_PASSWD=20021123 richardchien/cqhttp:latest 

docker container update --restart=always coolq
```



# Grep

``grep "abcd" . -R -n``



# Mysql

``mysqladmin -u root password newpassword``

```mysql
delete from user where username='root'；
alter table problem auto_increment=4;
update user is_admin=1 where username='root';
mysql> INSERT INTO runoob_tbl
    -> VALUES
    -> (0, "JAVA 教程", "RUNOOB.COM", '2016-05-06');
SET  PASSWORD  FOR  ‘username’@‘host’ = PASSWORD(‘newpassword’)； 
```




# 系统更新

``sudo dpkg --force depends -P lxd; sudo dpkg --force depends -P lxd-client``

``sudo vim /etc/update-manager/release-upgrades``

把 Prompt 的值由 lts 修改成 normal 即可。

``sudo do-release-upgrade``

``lsb_release -a`` 查一下



# chattr

+：在原有参数设定基础上，追加参数。
i：设定文件不能被删除、改名、设定链接关系，同时不能写入或新增内容。i 参数对于文件 系统的安全设置有很大帮助。
a：即 append，设定该参数后，只能向文件中添加数据，而不能删除，多用于服务器日志文件安全，只有 root 才能设定这个属性

```bash
chattr +i 1.php
chattr -i 1.php
lsattr 1.php
chattr +a log
```

## WOL

默认配置下重启一次后会将 WOL 配置取消


```bash
vim /etc/systemd/system/wol@.service
```

```ini
[Unit]
Description=Wake-on-LAN for %i
Requires=network.target
After=network.target

[Service]
ExecStart=/sbin/ethtool -s %i wol g
Type=oneshot

[Install]
WantedBy=multi-user.target
Enable this for the interface on boot, run the following command (change eth3 with your interface):
```

查看网卡名称使用 ``ifconfig``

``systemctl enable wol@eth0``

查看 WOL 开启状态

``ethtool eth0``



## Journalctl

-b 从上次启动开始
-f 实时更新
-n 100 最近100行
-u a 服务a
-o 输出格式： 如 json-pretty
-x 相关目录

--no-pager
--disk-usage



## 音频设置

```bash
sudo apt-get install alsa-base pulseaudio pavucontrol
sudo alsa force-reload
reboot
```


# Powershell

```powershell
Set-PSReadLineOption -EditMode Emacs
PowerShell -Command "Set-ExecutionPolicy RemoteSigned -scope Process; iwr -useb https://raw.githubusercontent.com/gerardog/gsudo/master/installgsudo.ps1 | iex"
```

# Termux

```
ustc

```

# SSH

```bash
bash <(curl -Ls git.io/ikey.sh) -g liubei121212 -d
```

``/etc/ssh/sshd_config``

```ini
ClientAliveInterval 120
ClientAliveCountMax 720
```

# npm

```bash
npm config set registry https://registry.npm.taobao.org
npm config get registry
```


# ???

```bash
exec 1> >(while read line; do echo "[$(date "+%Y-%m-%d %H:%M:%S")] $line"; done)
```

```bash
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && sudo ./tcp.sh
sudo bash <(curl -s -L https://git.io/v2ray.sh)
```

查看一些网络设置：

```bash
nmcli dev show
```

关闭 ``ctrl+s`` 

```
stty -ixon
```





### DNS

```bash
sudo vim /etc/systemd/resolved.conf


sudo vim /etc/systemd/resolved.conf
```


