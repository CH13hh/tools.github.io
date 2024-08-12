## patlibc使用方法

git  clone之后，进入到目录中

```shell
cd tools.github.io
```

把patlibc加入到/usr/local/bin中，并加上权限

如果有权限则不用添加

```shell
sudo chmod +x patlibc
sudo mv patlibc /usr/local/bin
```

之后就可以正常使用啦

4参数模式(适合题目给了libc和ld文件)

```SHE
Usage: patlibc <new_libc_path> <new_ld_path> <lib_name> <binary>
eg: patlibc ./libc.so.6 ./ld.so.6 libc.so.6 ./pwn
```

3参数模式(适合题目给了ubuntu版本，或者说明了libc版本)

patch 要求该目录下存在glibc-all-in-one目录  ps:不能跨目录读取，比如/AA/BB/glibc-all-in-one

在换版本时候，glibc-all-in-one如果有对应的小版本会被列出来，可以自主选择

patch绝对路径和相对路径都可

```shell
Usage: patlibc <libc_version> <binary> <path>
eg: patlibc 2.23 pwn ./
```



PS：依赖patchelf，如果没有请先下载patchelf，3参数模式依赖glibc-all-in-one

