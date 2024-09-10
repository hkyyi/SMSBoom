# SMSBoom

## 免责声明

1. 使用此程序请遵守当地的法律法规，禁止滥用、恶意使用，**触犯法律所造成的问题均由使用者承担**。
2. 本程序仅供娱乐，**禁止滥用** 和二次 **禁止用于商业用途**。

## Feature

1. 通过自定义 `api.json` 的方式定义接口.  
2. 支持关键字替换. **时间戳** `[timestamp]` **手机号** `[phone]`  
3. 多线程/异步 请求.  
4. 友好的命令行参数支持.  
5. 通过代理调用短信接口, 支持 http, socks4, socks5代理.
6. 使用随机的 User-Agent.
7. 可指定轰炸次数, 轰炸间隔时间.

## Quick Start

#### Step1. 下载 EXE 可执行文件

请移步到项目内下载smsboom.exe

#### Step2. 运行  

1. 在任意盘(**除C盘外**)中新建一个文件夹.将程序移动到其中. e.g.  

2. `Win`+`R` 打开cmd.输入存放的盘符.例如: `E:` 然后cd到文件夹,例如 `cd SMS`

3. 确认 cmd 路径是 EXE 所在路径后,cmd 输入:`smsboom.exe`,若出现命令提示,则说明脚本已正常运行.

4. 传递命令示例

启动64个线程,轰//炸一个人的手机号(198xxxxxxxx),只轰//炸一波。

```shell
smsboom.exe run -t 64 -p 198xxxxxxxxx
```

启动64个线程,轰//炸一个人的手机号(19xxxxxxx),启动循环轰//炸, 轮番轰//炸60次

```shell
smsboom.exe run -t 64 -p 198xxxxxxxxx -f 60
```

启动64个线程,轰//炸一个人的手机号(19xxxxxxx),启动循环轰//炸, 轮番轰//炸60次, 每次间隔30秒

```shell
smsboom.exe run -t 64 -p 198xxxxxxxxx -f 60 -i 30
```

启动64个线程,轰//炸一个人的手机号(19xxxxxxx),启动循环轰//炸, 轮番轰//炸60次, 每次间隔30秒, 开启代理列表进行轰炸

```shell
smsboom.exe run -t 64 -p 198xxxxxxxxx -f 60 -i 30 -e
```

启动64个线程,轰//炸多个人的手机号(138xxx,139xxxx),启动循环轰//炸, 轮番轰炸60次, 每次间隔30秒, 开启代理列表进行轰炸

```shell
smsboom.exe run -t 64 -p 138xxxxxxxx -p 139xxxxxxxx -f 60 -i 30 -e
```

## 命令行参数

- 运行:

```shell
# 输出帮助信息
smsboom.exe --help

Usage: smsboom.exe [OPTIONS] COMMAND [ARGS]...    
Options:
--help  Show this message and exit.
Commands:
run       传入线程数和手机号启动轰//炸,支持多手机号
asyncrun  以最快的方式请求接口(真异步百万并发)
onerun    单线程(测试使用)
```

- 启动轰//炸  

帮助信息:

```shell
smsboom.exe run --help

Usage: smsboom.exe run [OPTIONS]

传入线程数和手机号启动轰//炸,支持多手机号

Options:
-t, --thread INTEGER       线程数(默认64)
-p, --phone TEXT           手机号,可传入多个再使用-p传递  [required]
-f, --frequency INTEGER    执行次数(默认1次)
-i, --interval INTEGER     间隔时间(默认60s)
-e, --enable_proxy BOOLEAN 开启代理(默认关闭)
--help                     Show this message and exit.
```

### 使用代理

本项目不能通过API自动获取代理, 你可以从下面的免费代理网站中手动获取代理, 或是选择使用自己的代理, 或是不使用代理.

> [https://proxyscrape.com/free-proxy-list](https://proxyscrape.com/free-proxy-list)

> [https://openproxy.space/list](https://openproxy.space/list)

将代理添加到 `http_proxy.txt` `socks4_proxy.txt` `socks5_proxy.txt` 三个文件中, 命令参数添加 `-e` 执行即可.