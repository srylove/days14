linux 基础命令
mkdir 创建文件夹
pwd 查看工作目录
ping 检测主机
su 切换目录
cp 要复制的文件  目标路径
touch 创建一个空文件    
vi vim文件创建及编写
   :q-------------------如果未修改缓冲区数据，退出vim
   :wq------------------将缓冲区数据保存并退出vim
   :q!-------------------取消所有对缓冲区数据的修改并退出vim
   :w filename-------------将文件保存到另一个文件名下
rm 删除命令
cd 切换目录
ls 查看目录
 
reboot 重启
halt poweroff 关机

make 执行配置好的make文件
make clean 清除上次make生成的文件
例如：
hello : myhello.c   HelloPrint.c 
    gcc -o hello    myhello.c HelloPrint.c
clean:
    rm hello
上为make文件内容，执行make命令即可