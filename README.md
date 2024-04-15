---
描述: 简明 Nimble 挖矿指南
---

# Nimble 挖矿

使用这些配置说明去配置的硬件来挖NIM。

说明适用于 Linux, Windows 11, and Mac。

## 系统要求

推荐

* RTX 3090+ GPU
* Core i7 13700
* 16GB RAM
* 256 GB disk space

最低配置

* RTX 2080+ GPU (Linux/Windows), or M1/M2/M3 Mac chips
* Core i5 7400
* 16GB RAM
* 256 GB disk space

## 在 Windows 11 安装

### 安装 Golang

* 安装windows 子系统 (WSL)
  * [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
* 挖 Nimble 必需 Go 1.22.1. 如果你已经安装了golang老版本, 先删了它
  * `sudo apt-get remove golang-go`
  * `sudo rm -rf /usr/local/go`
* 完成后, 打开终端，执行下面命令
  * `cd /usr/local`
  * `sudo wget https://go.dev/dl/go1.22.1.linux-amd64.tar.gz`
  * `sudo tar -C /usr/local -xzf go1.22.1.linux-amd64.tar.gz`
  * `export PATH=$PATH:/usr/local/go/bin`
  * `go version`

应该能在终端看到显示: the go version 1.22.1

### 创建钱包

提示: 其余步骤需要使用git.

* 打开终端
* 执行下面的指令去下载钱包 CLI
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`
*  确保下面位置的文件存在 (用你的用户名替换 \<you>)
  * `/home/<you>/go/bin/nimble-networkd`
* 执行下面命令出创建你的钱包. 输入钱包名称, 譬如 'ilovenimble'.
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)`

输出打印“address: nimblexxxx” 意味着你的钱包地址成功生成!

### 开始挖矿


提示: python3.9 (或 更高版本) 和 pip3 在其余步骤必需要的

* 打开终端窗口
* 下载 python3 venv
  * `sudo apt update`
  * `sudo apt install python3-venv`

> 如果安装python3-venv挂了，或者有报错，清执行下面命令.
>
> ```shell
> sudo apt-get install software-properties-common
> sudo add-apt-repository ppa:deadsnakes/ppa -y
> sudo apt install python3-venv
> ```

* 下载并安装挖矿程序
  * `cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/nimble-miner-public.git`
  * `cd nimble-miner-public`
  * `make install`
  * `source ./nimenv_localminers/bin/activate`
  * `make run addr=<copy paste your “nimblexxx” wallet address here>`

机器挂了重新挖矿，重新跑这个命令：

`make run addr=<复制粘贴你的钱包地址 “nimblexxx”>`

## 在 Mac 安装

### 安装 Golang

* 下载安装 Golang (**v1.22 或更高**)
  * [https://golang.org/dl/](https://golang.org/dl/)
* 打开终端
* 执行下面命令
  1. `mkdir ~/go`
  2. `export GOPATH=$HOME/go`
  3. `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  4. `go version`

他应该显示go的版本, 比如. `goX.X.X darwin/amd64`

### 创建钱包

提示: 其余步骤需要使用git.

* 打开终端
* 执行下面命令去下载钱包cli工具
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`
* 确保下面位置的文件存在 (用你的用户名替换 \<you>)
  * `/Users/<you>/go/bin/nimble-networkd`
* 执行下面命令出创建你的钱包. 输入钱包名称, 譬如 'ilovenimble'.
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)`

输出打印“address: nimblexxxx” 意味着你的钱包地址成功生成!

### 开始挖矿

* 打开终端，执行下面命令
  * `cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/nimble-miner-public.git`
  * `cd nimble-miner-public`
  * `make install`
  * `source ./nimenv_localminers/bin/activate`
  * `make run addr=<copy paste your “nimblexxx” wallet address here>`

机器挂了重新挖矿，重新跑这个命令：

`make run addr=<复制粘贴你的钱包地址 “nimblexxx”>`

## 在 Linux 上安装和挖矿

### 安装 Golang

* 打开终端
* 执行下面命令
  * `sudo apt update`
  * `sudo apt install golang`
  * `export GOPATH=$HOME/go`
  * `export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin`
  * `go version`

It should display the go version.

### 创建钱包

提示: 其余步骤需要使用git.

* 打开终端
* 执行下面的命令去下载钱包 CLI
  * `mkdir $HOME/nimble && cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/wallet-public.git`
  * `cd wallet-public`
  * `make install`
*  确保下面位置的文件存在 (用你的用户名替换 \<you>)
  * `/home/<you>/go/bin/nimble-networkd`
  * Copy this path value and use it in the next step.
* 执行下面命令出创建你的钱包. 输入钱包名称, 譬如 'ilovenimble'.
  * `[nimble-networkd path]/nimble-networkd keys add ilovenimble`
  * `(Type your passphrase)`
  * `(Save the seed phrase somewhere safe)` The “address: nimblexxxx” output means your Nimble Network wallet address was created successfully!

### 开始挖矿

提示: python3.9 (或 更高版本) 和 pip3 在其余步骤必需要的

* 打开终端窗口，运行：
* 为 Linux 安装 python3 venv
  * `sudo apt update`
  * `sudo apt install python3-venv`

> 如果安装python3-venv挂了，或者有报错，清执行下面命令.
>
> ```shell
> sudo apt-get install software-properties-common
> sudo add-apt-repository ppa:deadsnakes/ppa -y
> sudo apt install python3-venv
> ```

* 打开终端窗口，运行：
  * `cd $HOME/nimble`
  * `git clone https://github.com/nimble-technology/nimble-miner-public.git`
  * `cd nimble-miner-public`
  * `make install`
  * `source ./nimenv_localminers/bin/activate`
  * `make run addr=<copy paste your “nimblexxx” wallet address here>`

机器挂了重新挖矿，重新跑这个命令：

`make run addr=<复制粘贴你的钱包地址 “nimblexxx”>`

## 祝贺 😘

你现在可以挖 NIM!

如需帮助，请访问我们的 Discord 服务器 - [https://discord.gg/nimble](https://discord.gg/nimble)
