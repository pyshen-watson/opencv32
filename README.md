# Task: OpenCV in C language with 32-bit version

## Goal
- 找到任意一個opencv的API (如讀一張圖片)，能夠成功在c語言的程式中引用、編譯及呼叫

## Note

### 用gcc編譯32bit
- 如果要在64bit系統上跑32bit，要先`sudo apt-get install libc6-dev-i386`
- 編譯時要加 `-m32`, ex. `gcc -m32 main.c -o main.exe`

### 安裝32bit的C++
- 裝了這個才能編譯opencv
```
sudo apt-get update
sudo apt-get install g++-multilib
```

### 安裝32bit的opencv
- 嘗試方法一: 從[官網](https://opencv.org/releases/)下載Source code自己編譯
    1. 下載zip檔 (v3.4.15)
    2. 用`unzip`指令解壓縮
    3. 進入解壓縮的目錄(`cd opencv-3.4.15`)
    4. 建立並進入build目錄 (`mkdir build && cd build`)
    5. 使用cmake編譯 (`cmake -DCMAKE_C_FLAGS=-m32 -DCMAKE_CXX_FLAGS=-m32 -DCMAKE_INSTALL_PREFIX=/usr/local ..`)
        1. 前兩個flag是指編譯成32-bit
        2. `-DCMAKE_INSTALL_PREFIX`是安裝的路徑
        3. `..`是回到上層目錄尋找`cMakeList.txt`
    6. 跑完之後`build`內會有很多`.cmake`檔，但找不到`.so`或`.h`檔，`/usr/local`裡也沒有 (待修)

- 嘗試方法二: 用`sudo apt-get install libopencv-dev`安裝開發套件
    1. `/usr/include/opencv4/opencv2`內會有很多的`.hpp`檔，但不知道能不能用

