# 注意事项：
⚠️⚠️保持 sing-box 以官方裸核形式运行，追求极致精简与性能⚠️⚠️  
Sbshell 是一款针对 官方sing-box 的辅助运行脚本，旨在解决官方sing-box的使用不便：

- 支持系统为Debian/Ubuntu/Armbian以及OpenWrt。
- 运行脚本如遇到缺少curl和bash，请自行安装后再运行脚本。
- 默认为禁用开机自启动，可在菜单中开启自启动，如果禁用自启动需要重启singbox。
- 默认后端、订阅、规则 需要在菜单中自行设置。
- 使用自建节点不需要订阅转换的用户，后端和订阅输入为空，规则使用自己的配置文件地址即可。
- 如果使用自己的配置文件需要注意tproxy配置文件中需要定义两个参数和脚本中一致：     入站中的tproxy监听端口必须为："listen_port": 7895,，route模块必须添加mark标记："default_mark": 666,
- 如果使用的pve-lxc容器，请开启特权模式，否则tun模式内核无法创建防火墙规则，建议使用正常的虚拟机。
- 面板自动更新优先配置文件定义，如果未定义则使用默认值Zephyruso面板
- 更新singbox后，请reboot下系统
- 官方openwrt商店的singbox版本比较低，使用提供的配置请自行替换内核为1.11，或用自己的低版本配置文件。

## 一键脚本：(请自行安装curl和bash，如果缺少的话)
```
bash <(curl -sL https://gh-proxy.com/https://raw.githubusercontent.com/qljsyph/sbshell/refs/heads/main//sbshall.sh)
```
- 初始化运行结束，输入“**sb**”进入菜单
- 目前支持系统为deiban/ubuntu/armbian/openwrt。  
- 防火墙仅支持nftables，不支持iptables。

### 系统信息自动显示美化脚本： 
```
bash <(curl -sL https://gh-proxy.com/https://raw.githubusercontent.com/qljsyph/DPInfo-script/refs/heads/main/auto-sysinfo.sh)
```
  执行后每次进入ssh会自动显示很多必要信息！
  仓库：  
  https://github.com/qljsyph/DPInfo-script

## 适配配置文件：

### 稳定版(1.11)：  
tproxy：  
https://gh-proxy.com/https://github.com/yeqiu233/sbshellcopy/blob/main/config_template/config_tproxy.json

tun：  
https://gh-proxy.com/https://github.com/yeqiu233/sbshellcopy/blob/main/config_template/config_tun.json

### 部分省份电信对联通IP进行屏蔽，这个是专属解决方案
tun：  
https://gh-proxy.com/https://github.com/yeqiu233/sbshellcopy/blob/main/config_template/config_tun_dianxin.json

## 卸载singbox裸核：

### debian卸载：
```
sudo apt-get remove --purge -y sing-box sing-box-beta
sudo rm -rf /etc/sing-box
```
### openwrt卸载：
```
opkg remove --purge sing-box
rm -rf /etc/sing-box
```
