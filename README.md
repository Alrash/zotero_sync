# Zotero Sync

## 编写目的  
利用现有服务器同步两台PC  

## 动机  
> 1. 实验室一台PC，宿舍一台笔记本
> 2. 校园网中存在一台工作站，可以内网/外网（ssh 反向隧道连接外网服务器，但速度较慢）通过SSH协议访问
> 3. 搜了一下坚果貌似连接也很慢
> 4. **干脆使用SSH利用工作站做“云”存储，两台设备直接通过工作站同步storage文件夹**
> 5. 宿舍使用，也是在回宿舍之后，可以定时上传实验室的去工作站上

## 满足以下使用需求，即可使用  
> 1. 多设备需要论文的情况
> 2. 拥有一台可通过SSH协议访问的服务器（速度取决于服务器）
> 3. 可使用*上传/下载/同步*任意一种方式进行本地文件“同步”

## python包依赖
> * paramiko

## 缺点
不会自动同步/按时同步，当前只能手动同步  
您可以使用系统自带如systemctl(linux), 任务计划(windows)等进行定时同步

## 如何使用  
### 配置文件 
```json
{
  "username": "your user name",
  "passwd": "your password",
  "ssh_config": {
    "host": "host or ip address",
    "port": 22,
    "auth": "on or off",
    "key": "private key path",
    "passwd": "private key password"
  },
  "local": "local zotero root path, like ~/zotero (~/zotero/storage, ~/zotero/style, ..., and so on)",
  "remote": "remote server save directory",
  "sync": "up or down or sync"
}
```
> * port: default 22, and should be int
> * if private key password not set, it could be none
> * auth: if choose on, program will attempt to connect with user password if private key path dont exist

### 参数选项  
**参数选项优先于配置文件**  
```
-c [config file path]
-u [username]
-w [user password]
-i [host]
-p [port]
-k [private key path]
-W [private key password]
-l [local zotero root path]
-r [remote sync directory]
-s [sync choice: up / down / sync]
-a [auth choice: on / off]
```

## LICENSE
MIT
