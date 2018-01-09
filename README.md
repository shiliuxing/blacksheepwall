blacksheepwall
===

[![](https://godoc.org/github.com/tomsteele/blacksheepwall/bsw?status.svg)](http://godoc.org/github.com/tomsteele/blacksheepwall/bsw)

blacksheepwall是一款由Go语言编写的域名信息搜集工具 ，你也可以在你的工具中将它作为一个独立软件包来使用。

## 下载

blacksheepwall支持跨平台，目前它所支持的系统有windows、linux以及苹果的darwin。你可以在[这里下载](https://github.com/tomsteele/blacksheepwall/releases/tag/v3.3.0)到不同版本的二进制软件包。

## 安装

你可以直接下载编译好的二进制文件运行并安装它。如果你的系统已经安装好了Go语言环境并配置好了工作区，那么你也可以直接通过以下命令下载安装：

$ go get github.com/tomsteele/blacksheepwall

## 使用

```
Usage: blacksheepwall [options] <ip address or CIDR>
命令选项:

 -h, --help            显示帮助信息并退出
 -version              显示当前版本信息并退出
 -debug                启用调试并显示从任务返回的错误。
 -config               包含以下任何选项的YAML文件的位置。
                       连字符使用下划线代替 (例如 bing-html, bing_html).
                       没有参数的选项为布尔值应该使用true/false表示（例如bing_html：true）
 -timeout              SOCKET连接的最大超时时间（以秒为单位）[默认.5秒]
 -concurrency <int>    最大并发任务数 [默认：100]
 -server <string>      DNS服务器地址 [默认：“8.8.8.8”]
 -input <string>       以行分隔的CIDR或IP地址文件
 -ipv6                 寻找更多适用的AAAA记录
 -domain <string>      用于某些任务的目标域可以是单一的也可以是以行分隔的域名文件
 -fcrdns               通过尝试检索先前确定的每个主机的A或AAAA记录来验证结果
 -parse <string>       通过从先前扫描的文件中解析JSON来生成输出
 -validate             使用符合RFC的正则表达式验证主机名
Passive:
 -dictionary <string>  尝试检索以行分隔文件中子域的CNAME和A记录
 -ns                   查找域的所有域名服务器的IP和主机名
 -mx                   查找域的任何mx记录的ip和hostmame。
 -yandex <string>      提供了一个Yandex搜索XML API url，使用Yandex
                       搜索“rhost：”查找目标域的子域
 -bing <string>        提供了一个base64编码的API密钥，使用必应搜索
                       API的'ip：'来查找每个ip的主机名，而
                       'domain：'来查找域的ips/hostnames
 -bing-html            使用Bing搜索“ip：”来查找每个ip的主机名，而
                       'domain：'查找域的ips/hostnames
                       
 -shodan <string>      提供了一个Shodan API密钥，使用Shodan的API'/dns/reverse'来查找每个IP的主机名
                       '/shodan/host/search'查找一个域的ips/hostnames，对所有IP都进行一次调用
                       
 -reverse              检索每个主机的PTR
 -viewdns-html         使用viewdns.info的IP反向查找功能查询zhu'ji主机，请谨慎使用否则会被封杀
 -viewdns <string>     使用viewdns.info的API和IP反向查找功能查找每个主机。
 -logontube            使用logontube.com的API查找主机和（或）域，截至本次发布
                       该网站已被关闭
 -exfiltrated          查找从exfiltrated.com的主机名搜索返回的主机名
 -censys <string>      搜索censys.io域。名称的收集来自于这个搜索的每个主机的TLS证书。该命令选项后跟的字符串为API ID和Secret并用冒号分隔
 -crtsh                在crt.sh中搜索与所提供域相关的证书
 -vt                   在提供域的子域名中搜索VirusTotal
 -srv                  查找DNS SRV记录并检索关联的主机名/ IP信息
 -cmn-crawl <string>   搜索commoncrawl.org域的子域。提供索引要使用参数
                       。例如：“CC-MAIN-2017-04-index”
Active:
 -axfr                 尝试域的区域传输
 -headers              对每个主机执行HTTP（s）请求并查找
                       可能位置中的主机名
 -tls                  尝试从TLS证书中检索名称
                       （公用名称和主题备用名称）
Output Options:
 -clean                打印结果为每个主机的主机名
 -csv                  打印结果为csv格式
 -json                 打印结果为JSON
 ```
