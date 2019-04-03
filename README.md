Nvidia Docker installation 
=======
這份Readme是從零開始，安裝Ubuntu 18.04到docker的安裝、使用及開放外部使用者可以使用ipvr實驗室虛擬機的port在CUDA下以加速完成你要執行的任務
- linux setup 18.04
- NVIDIA driver
- cuda
- docker
- docker image
- shell script
- vscode  //work_env

# 1.	先裝好Ubuntu如下網站所示
先製作Live USB隨身碟的軟體Unetbootin，如下網站所示

教學網站：https://blog.xuite.net/yh96301/blog/57645340-Ubuntu+18.04%E8%A3%BD%E4%BD%9CLive+USB%E9%9A%A8%E8%BA%AB%E7%A2%9F%E7%9A%84%E8%BB%9F%E9%AB%94Unetbootin

以USB安裝Ubuntu的步驟

教學網站：https://blog.xuite.net/yh96301/blog/242333268

裝好後請記得 reboot 謝謝

# 2. Ubuntu 18.04 安裝NVIDIA驅動程式

教學網站：http://chiustin.blogspot.com/2019/01/ubuntu-1804-nvidia.html

安裝前的套件

```shell
sudo apt-get install gcc
sudo apt-get install make
```
下面這行用以退出可能正在使用GPU的任何程序，才能進行安裝nvidia-driver

```shell
sudo service gdm3 stop
```

若沒執行可能會在安裝時出錯，如下

```shell
ERROR: An NVIDIA kernel module 'nvidia-drm' appears to already be loaded in your kernel.
This may be because it is in use (for example, by an X server, a CUDA program, or the NVIDIA Persistence Daemon), 
but this may also happen if your kernel was configured without support for module unloading.
Please be sure to exit any programs that may be using the GPU(s) before attempting to upgrade your driver.
If no GPU-based programs are running, you know that your kernel supports module unloading, 
and you still receive this message, then an error may have occured that has corrupted an NVIDIA kernel module's usage count, 
for which the simplest remedy is to reboot your computer.
```
記得重新啟動你的裝置
```shell
reboot
```
安裝驅動

```shell
sudo add-apt-repository ppa:graphics-drivers/ppa 
sudo apt-get update
sudo apt-get install nvidia-driver-418
sudo service gdm3 start
reboot
```
進入桌面，執行下面的命令，查看驅動的安裝狀態
```shell
sudo nvidia-smi
```

若有安裝成功應該出現以下畫面

![image](https://github.com/ncuipvr/RoadToHell/blob/master/im/ubuntu%20driver-device.png)
