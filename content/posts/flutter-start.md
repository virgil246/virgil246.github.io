---
title: "Flutter Start"
date: 2020-09-02T11:15:00+08:00
tags: ["Flutter"]
categories: ["教學"]
draft: false
---
# [安裝](https://flutter.dev/docs/get-started/install)

## [以Windows為例](https://flutter.dev/docs/get-started/install/windows)

* [系統需求](https://flutter.dev/docs/get-started/install/windows#system-requirements)

1. 下載Flutter SDK  
  * 要記得解壓縮後或clone下來的`PATH`
    1. [直接下載](https://storage.googleapis.com/flutter_infra/releases/stable/windows/flutter_windows_1.20.3-stable.zip)
    2. `git clone https://github.com/flutter/flutter.git -b stable`
2. 更新系統路徑  
   1.  
   ![](https://i.imgur.com/k6LNLZU.png)
   2. 環境變數
   ![](https://i.imgur.com/gFuEc08.png)
   3. 編輯Path這一項
   ![](https://i.imgur.com/b94pDhK.png)
   4. 加入 ![](https://i.imgur.com/q6ag2xh.png)
    > 記得是要按照你第一步放Flutter的`PATH` 來更新這裡的使用者變數
3. 到此  可以開啟 Windows Terminal, Powershell or cmd
Run `flutter doctor` 如果需要更詳細的除錯資訊 `flutter doctor -v`
    > 可以見到一些訊息
    ```
    [-] Android toolchain - develop for Android devices
        • Android SDK at D:\Android\sdk
        ✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ
        • Try re-installing or updating your Android SDK,
        visit https://flutter.dev/setup/#android-setup for detailed instructions.
    ```
> Note: Flutter relies on a full installation of Android Studio to supply its Android platform dependencies. However, you can write your Flutter apps in a number of editors; a later step discusses that.
4. 安裝[Android Studio](https://developer.android.com/studio)

# [設定IDE](https://flutter.dev/docs/get-started/install)

>有問題可以在下方utterances 留言喔
