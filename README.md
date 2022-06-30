## npm与vue

### 安装,卸载cli3
  卸载cli3
```
npm uninstall -g @vue/cli
```
  安装cli3
```
npm install -g @vue/cli
```
### npm设置
 修改下载仓库为淘宝镜像
``` 
npm config set registry http://registry.npm.taobao.org/
```
 如果要发布自己的镜像需要修改回来
```
npm config set registry https://registry.npmjs.org/
```

### 创建Vue工程
#####  UI界面创建工程
```
vue ui
```
  安装ui界面
```
npm install -g @vue/cli
```
#####  npm命令创建Vue工程
```
vue init webpack filename
```
    ? Project  vue-demo # 项目名称，直接回车，按照括号中默认名字（注意这里的名字不能有大写字母，如果有会报错Sorry,  can no longer contain capital letters）
    ? Project description A Vue.js project # 项目描述,随便写
    ? Author # 作者名称
    ? Vue build standalone # 我选择的运行加编译时
    	Runtime + Compiler: recommended for most users
    ? Install vue-router? Yes # 是否需要 vue-router，路由肯定要的
    ? Use ESLint to lint your code? Yes # 是否使用 ESLint 作为代码规范.
    ? Pick an ESLint preset Standard # 一样的ESlint 相关
    ? Set up unit tests Yes # 是否安装单元测试
    ? Pick a test runner 按需选择 # 测试模块
    ? Setup e2e tests with Nightwatch? 安装选择 # e2e 测试
    ? Should we run `npm install` for you after the project has been created? (recommended) npm # 包管理器，选的NPM--

### 项目运行
 安装依赖
```
npm install
```
  建议不要直接使用 cnpm 安装以来，会有各种诡异的 bug。可以通过如下操作解决 npm 下载速度慢的问题
```
npm install --registry=https://registry.npm.taobao.org
```
  启动服务
```
npm run dev
```
  构建生产环境
```
npm run build:prod
```

## 安卓
#### 生成安卓密钥
  使用keytool -genkey命令生成证书：
```
keytool -genkey -alias testalias -keyalg RSA -keysize 2048 -validity 36500 -keystore filname.keystore
```
`testalias 是证书别名，可修改为自己想设置的字符，建议使用英文字母和数字,可能类似证书账户？
test.keystore 是证书文件名称，可修改为自己想设置的文件名称，也可以指定完整文件路径
36500是证书的有效期，表示100年有效期，单位天，建议时间设置长一点，避免证书过期`
  查看证书信息
```
keytool -list -v -keystore filname.keystore
```
## linux命令
  删除回收站
```
sudo rm -rf ~/.local/share/Trash/*
```
#### linux打开docker运行镜像
  docker拉去epic自动镜像
```
docker pull luminoleon/epicgames-claimer
```
  docker打开自动 每次需要登录
```
docker run -it luminoleon/epicgames-claimer
```


  docker打开自动 一次登录
```
docker run -it -v ~/epicgames_claimer/User_Data:/User_Data luminoleon/epicgames-claimer
```
  云服务器创建窗口
```
screen -S docker
```
  云服务器恢复窗口
```
screen -r docker
```

#### ubuntu安装nginx
  切换至root用户
```
sudo su root
```
```
apt-get install nginx
```
  查看nginx是否安装成功
```
nginx -v
```
#### linux修改root账户登录
  切换至root用户
```
sudo su root
```
  打开配置文件
```
sudo vi /etc/ssh/sshd_config
```
PermitRootLogin yes
esc :wq
  重启 ssh 服务。
```
sudo service ssh restart
```
#### linux运行nginx
  执行以下安装命令
```
sudo apt-get install nginx
```
  安装完成，查看版本来检测是否安装成功。
```
sudo apt-get install nginx
```

```
nginx文件安装完成之后的文件位置：
    /usr/sbin/nginx：主程序
    /etc/nginx：存放配置文件
    /usr/share/nginx：存放静态文件
    /var/log/nginx：存放日志
 ```

  修改配置后重新加载生效  
```
nginx -s reload
```
  重新打开日志文件
```
nginx -s reopen
```
  测试nginx配置文件是否正确
```
nginx -t -c /path/to/nginx.conf
```
关闭nginx
快速停止nginx
```
nginx -s stop
```
完整有序的停止nginx
```
nginx -s quit
```

其他的停止nginx 方式：
```
ps -ef | grep nginx
kill -QUIT 主进程号     ：从容停止Nginx
kill -TERM 主进程号     ：快速停止Nginx
pkill -9 nginx          ：强制停止Nginx
启动nginx:
nginx -c /etc/nginx/nginx.conf
平滑重启nginx：
kill -HUP 主进程号
```

  启动nginx
```
service nginx start
```
  关闭nginx：
```
nginx -s stop
```

#### linux中screen分屏
  安装screen
```
sudo apt install screen
```
  新建名字为qszl的窗口
```
screen -S qszl
```
  分离会话
快键键Ctrl+a+d实现分离 或者
```
screen -ls
```
  恢复名字为qszl的窗口
```
screen -r qszl 或 screen -r 27582
```
  杀死会话窗口
```
kill -4406 threadnum
```
  清除死去窗口
```
screen -wipe
```
#### openvpn
 停止openvpn
```
killall openvpn
```
  cd到目录
```
/usr/sbin
```
  以配置启动
```
openvpn --cd /etc/openvpn/server --config server_udp.conf
```
```
openvpn --cd /etc/openvpn/server --config server_tcp.conf
```

## CMD--Bat命令
  创建日期文件夹bat
```
set "ymd=%date:~0,4%%date:~5,2%%date:~8,2%"
set "hms=%time:~0,2%%time:~3,2%%date:~8,2%"
md D:\temp\class%ymd%_%hms%
```
 管理员安装msi 
```
msiexec /package "mysql.msi"
```
  host文件夹位置
```
C:\Windows\System32\drivers\etc
```

## zerotier虚拟局域网
显示自己在的局域网列表
```
sudo zerotier-cli listnetworks
```
安装
```
curl -s https://install.zerotier.com | sudo bash
```
添加进局域网,在网页上创建好虚拟网络,将命令中的 xxxxxxxx 替换成实际的虚拟网络 ID。
```
sudo zerotier-cli join xxxxx
```
配置 Moon,进入 zerotier-one 程序所在的目录，默认为 /var/lib/zerotier-one。
```
cd /var/lib/zerotier-one
```
生成 moon.json 配置文件
```
sudo zerotier-idtool initmoon identity.public >> moon.json
```
编辑 moon.json 配置文件,将配置文件中的 "stableEndpoints": [] 修改成 "stableEndpoints": ["ServerIP/9993"]，将 ServerIP 替换成云服务器的公网IP。
```
nano moon.json
```
生成 .moon 文件
```
sudo zerotier-idtool genmoon moon.json
```
将生成的 000000xxxxxxxxxx.moon 移动到 moons.d 目录
```
sudo mkdir moons.d
```
```
sudo mv 00000039a92389e2.moon moons.d
```
重启 zerotier-one 服务
```
sudo systemctl restart zerotier-one
```
客户端加入
普通的 Zerotier 成员使用 Moon 有两种方法，第一种方法是使用 zerotier-cli orbit 命令直接添加 Moon 节点ID；第二种方法是在 zerotier-one 程序的根目录创建moons.d文件夹，将 xxx.moon 复制到该文件夹中，我们采用第一种方法：
将命令中的两组 xxxxxxxxxx 都替换成 moon 的节点ID。先下载安装,再
```
zerotier-cli orbit xxxxxxxxxx xxxxxxxxxx
```

## linux部署
安装 32 位运行库
如果你使用的是 64 位的系统，则需要安装 32 位的运行库。
```
sudo apt-get install lib32gcc1
```
下载 Left 4 Dead 2 Dedicated Server
```
mkdir ~/steamcmd
```
```
cd ~/steamcmd
```
```
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
```
```
tar -zxvf steamcmd_linux.tar.gz
```
```
./steamcmd.sh
```
指定下载目录
```
force_install_dir /home/ubuntu/l4d2
```
完成后，匿名登陆服务器。（某些game不能匿名登陆下载，具体看这 https://developer.valvesoftware.com/wiki/Dedicated_Servers_List）
```
login anonymous
```
下载服务端，下载指令是 app_update <app_id> [-beta ] [-betapassword ] [validate] app_id 可以在上面的链接找到。
```
app_update 222860 validate
```
下载完成后会提示 Success! App '222860' fully installed.，这时候输入 quit 退出即可。

需要安装 SourceMOD 和 MetaMOD
https://www.sourcemod.net/downloads.php?branch=stable
http://metamodsource.net/downloads.php?branch=stable

```
cd /home/ubuntu/l4d2/left4dead2
```
```
wget https://sm.alliedmods.net/smdrop/1.10/sourcemod-1.10.0-git6454-linux.tar.gz
```
```
wget https://mms.alliedmods.net/mmsdrop/1.10/mmsource-1.10.7-git971-linux.tar.gz
```
之后解压：
```
tar xvf sourcemod-1.10.0-git6454-linux.tar.gz
```
```
tar xvf mmsource-1.10.7-git971-linux.tar.gz
```
继续放插件

新建/恢复名字为qszl的窗口
```
screen -S qszl
screen -r qszl
```
启动脚本返回到有srcds_run这个东西所在的目录。

```
cd /home/ubuntu/l4d2
```
```
./srcds_run -game left4dead2 -insecure +exec server.cfg -console +port 27015 +exec server.cfg +map c2m1_highway
```
来具体解释一下，srcds_run 就是启动服务端用的；game 参数不多说了；insecure 是禁用 VAC，一些客户端的 mod 不禁用这个的话容易被制裁，比如说自动 BunnyHop 的 mod；port 是端口，默认是27015，建议修改；condebug 是输出 debug 的信息；exec 是执行前面写的server.cfg；nomaster 同样是隐藏服务器用的。
给这个启动脚本加上权限：
## 安装cloudreve
https://github.com/cloudreve/Cloudreve/releases
到网址下载tar.gz文件，并发送到服务器/home/ubuntu
新建/恢复名字为cloudreve的窗口
```
screen -S cloudreve
screen -r cloudreve
```
cd到文件目录

```
cd /home/ubuntu
```
解压获取到的主程序
```
tar -zxvf cloudreve_VERSION_OS_ARCH.tar.gz
```
赋予执行权限
```
chmod +x ./cloudreve
```
启动 Cloudreve
```
./cloudreve
```

## hunder
1.Ubuntu安装jdk1.8
更新软件源
```
sudo apt-get update
```
安装openJDK1.8
```
sudo apt-get install -y openjdk-8-jdk
```
查看版本
```
java -version
```
显示 "openjdk version "1.8.0_252"就表示安装完成

2.下载最新版的dst-admin.jar安装包
进入到home目录
```
cd ~
```
下载安装包
```
wget http://clouddn.tugos.cn/release/dst-admin-1.4.0.jar -O dst-admin.jar
```
3.启动dst-admin
```
java -jar dst-admin.jar
```
出现了Completed initialization表示启动成功，按Control+C键结束进程

4.安装饥荒客户端
启动完成的dst-admin将释放两个脚本：install.sh 用于安装客户端 ,dstStart.sh 用于管理饥荒管理平台
同时会生成一个网页管理平台,地址为ip:8080

执行安装饥荒客户端安装程序,期间可能需要输入密码，这一步必须执行成功
```
cd ~
```
```
./install.sh
```
执行管理脚本
```
cd ~
```
```
./dstStart.sh
```


