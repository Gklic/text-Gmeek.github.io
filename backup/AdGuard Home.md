#禁用systemd-resolved
53端口是DNS默认端口，正常情况不建议更改，否则配置DNS时地址为 ip+端口，比较麻烦
systemd-resolved 占用了53端口，需禁用[1]

# 停用服务
`systemctl stop systemd-resolved`
# 使用Vim编辑配置文件
`vi /etc/systemd/resolved.conf`
# 接下来，按下 i （进入编辑模式），用键盘上的方向键控制光标，把# DNSStubListener=yes前面的#去掉，然后把yes改为no
# 按下 esc 输入 :wq 回车即可（保存并退出）
# 运行下方命令
`ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf`

#AdGuardHome一键部署

`curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v`

#或者通过wget下载程序主文件并解压
`wget https://static.adguard.com/adguardhome/release/AdGuardHome_linux_amd64.tar.gz
`
`tar xvf AdGuardHome_linux_amd64.tar.gz`
#解压完成后，进入解压出来的目录。
`cd AdGuardHome`
#需要注意的是，如果你不是root用户，就一定要按照下面命令行这样，加上sudo安装服务。
`sudo ./AdGuardHome -s install`