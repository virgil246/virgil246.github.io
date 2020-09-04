---
title: "Chocolatey 安裝"
date: 2020-09-04T23:01:20+08:00
draft: false
categories: ["教學"]
tags: ["Chocolatey","Windows"]
---


# 簡介
* [官方網站](https://chocolatey.org/)
> The Package Manager for Windows
* 就如同Ubuntu有 [apt](https://zh.wikipedia.org/wiki/APT) 、CentOS有 [yum](https://zh.wikipedia.org/wiki/Yellowdog_Updater,_Modified)、MacOSX有[Homebrew](https://brew.sh/index_zh-tw) Windows也有套件安裝管理工具 => **Chocolatey**
* 套件管理工具
  * 指令安裝套件工具
  * 省去自己設定的麻煩
# 安裝流程
1. [官方安裝流程](https://chocolatey.org/install)
* Requirements
  * Windows 7+ / Windows Server 2003+
  * PowerShell v2+ (minimum is v3 for install from this website due to TLS 1.2 requirement)
   * .NET Framework 4+ (the installation will attempt to install .NET 4.0 if you do not have it installed)(minimum is 4.5 for install from this website due to TLS 1.2 requirement)
2. 我們就從最簡單的開始  **以系統管理員安裝**
3. 用系統管理員身分開啟PowerShell 
![](https://i.imgur.com/gJTJPue.png)
看到`PS C:\WINDOWS\system32>`就是系統管理員權限了
4. 執行這行
    ```Powershell
    Get-ExecutionPolicy
    ```
    如果看到 `Restricted` 則執行
    ```Powershell
    Set-ExecutionPolicy AllSigned
    ```
    或
    ```Powershell
    Set-ExecutionPolicy Bypass -Scope Process
    ```
5. 執行這行開始安裝
    ```Powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    ```
6. 等他跑完也沒出現錯誤就安裝完成了  
7. 可以執行`choco` 或 `choco -?`
查看如何使用chocolatey
>有問題可以在下方utterances留言喔
