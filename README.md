# scan

## 功能:

多线程端口，获取 banner 信息
提取 HTTP HTTPS 协议中的有效信息，返回头中 Server、Location， 返回体中 <title>
通过 NBNS 协议获取主机名 (UDP 137)
Redis 检测未授权
MS17-010 检测 (抄了巡风的脚本)
通过 445 检测 Windows 的版本 (抄了 17-010 的 PHP 脚本)
  
## 用法:

python scan.py ip [-o nt] [-p 80,81-85,...]
ip 可以是 单个ip、CIDR 或者 192.168.0.0-255 这种形式 -o 选项 n 就是使用 nbns 探测主机名，t 就是探测 TCP端口，默认是同时探测 -p 指定 TCP 的端口

## 例子:

python scan.py 10.19.38.0/24
扫描 10.19.38.0/24 的默认端口，并获取主机名

python scan.py 10.19.38.0/24 -o n
获取 10.19.38.0/24 的主机名，不扫描 TCP 端口

python scan.py 10.19.38.0/24 -p 22,23-25
扫描 10.19.38.0/24 的 TCP 22,23,24,25 端口，获取主机名
