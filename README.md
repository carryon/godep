# godep
管理golang项目的依赖包

## 环境

- 本项目编译之前，需用户自行安装`Golang`；
- 编译时间视具体网络环境而定；
- 要求`linux`或`macos`系统即可。

## 说明

- 该工具依赖yaml文件依次拉去依赖包，不支持间接依赖包的自动获取(需用户把间接依赖的包手动维护到yaml中).
- 该工具支持并发下载依赖包，支持repo和version参数的设置.
- 运行工具时，程序自动检查当前目录下的yaml文件(文件格式如`example/godep.yaml`).
- 本工具支持依赖glide.yaml文件下载依赖包(仅限文件中定义的包).

## 使用

- 一般通过glide工具建立glide.yaml.
- 手动完善glide.yaml中的间接依赖包.
- 在glide.yaml文件的目录下用godep工具下载依赖包(自动放入vendor下).

## 优势

- 相比glide工具，本工具支持并发下载，提高了下载效率.
- 对于一些受限包，例如`golang.org/x/crypto/ssh`，本工具不会再去连接，而是依赖repo参数重定向.
- 相对glide, gomod而言，本工具很轻量.

## 获取

git clone https://github.com/dongjialong2006/godep.git

## 编译

- make

## 安装

- 将godep放到PATH所引到的bin目录下即可.
- go get -u github.com/dongjialong2006/godep

## 命令

支持的参数
- update: 表示更新未下载的包.
- version: 查看当前版本.

执行命令
- godep or godep update or godep -update

## 注意

该工具不支持`subpackages`命令，例如：

***
- package: golang.org/x/crypto/ssh
- repo: https://github.com/golang/crypto.git
- subpackages:
  - ssh
***
应改成：

***
- package: golang.org/x/crypto
- repo: https://github.com/golang/crypto.git
***
