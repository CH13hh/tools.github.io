## patlibc 安装与使用

`patlibc` 是一个用于简便替换 `libc` 库的工具，适用于解决需要自定义 `libc` 的 `pwn` 题目。  
**注意：** 依赖 `patchelf`，若未安装，请先下载 `patchelf`。三参数模式依赖 `glibc-all-in-one`。

### 安装方式

```shell
git clone https://github.com/CH13hh/tools.github.io 
cd tools.github.io 
sudo chmod +x patlibc 
sudo cp patlibc /usr/local/bin
```

完成上述步骤后即可使用。

### 使用方法

**注：** 使用 `patlibc` 时需要在 `pwn` 题目所在的文件夹下，否则可能出现替换失败。
**注：** 使用 `patlibc` 时需要在 `pwn` 题目所在的文件夹下，否则可能出现替换失败。
**注：** 使用 `patlibc` 时需要在 `pwn` 题目所在的文件夹下，否则可能出现替换失败。


**方法一：四参数模式**（适用于题目提供了 `libc` 和 `ld` 文件）

```shell
Usage: patlibc <new_libc_path> <new_ld_path> <lib_name> <pwn_name> 

eg: patlibc ./libc.so.6 ./ld.so.6 libc.so.6 ./pwn
```

**方法二：三参数模式**（适用于使用 `glibc-all-in-one` 来替换 `libc` 库）

该模式需要指定 `libc` 版本（必须是 `glibc-all-in-one` 的 `libs` 文件夹中已有的）。例如，`2.23-0ubuntu11.3_amd64`，则 `参数一` 填写 `2.23` 即可。

**注：**如果有多个小版本，则可以自行选择，path不能跨目录读取，比如../AA/BB/glibc-all-in-one

假设 `glibc-all-in-one` 在 `~/` 文件夹中，则参数三填写 `~/`。

```shell
Usage: patlibc <libc_version> <pwn_name> <glibc-all-in-one_path> 

eg: patlibc 2.23 pwn ~/
```