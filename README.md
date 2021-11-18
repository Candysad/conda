# conda

## 一个python环境的版本控制工具

创建不同环境并实现对它们的管理，使得一台机器上同时可以存在多个相同软件包版本不同的环境



### 版本

- Anaconda
  - 更完整，提供更多的软件包下载；
- miniconda
  - 提供更少的软件包；
  - 更精简；
- 两者使用方法相同



### 修改下载源

- tuna：[ Anaconda源帮助页](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)

- 修改用户目录下的 `.condarc` 文件

- Windows环境下无法直接创建名为`.condarc`的文件，先执行如下命令

  ```powershell
  conda config --set show_channel_urls yes
  ```

  会在用户目录下创建该文件

- 将以下内容添加至该文件以将下载源切换至tuna

  ```
  channels:
    - defaults
  show_channel_urls: true
  default_channels:
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
  custom_channels:
    conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  ```



### 创建一个环境

语法

```powershell
conda create --name <env> --file <this file>
```

例

```powershell
conda create --name d2l python=3.8 -y
```

该例创建了一个名为d2l的环境，并指定python版本为3.8



### 激活一个环境

例

```powershell
conda activate testenv
```



### 关闭一个环境

例

```powershell
conda deactivate testenv
```

使用该命令会回到base环境



### 列出所有环境

例

```powershell
conda env list
```



### 删除一个环境

例

```powershell
conda remove --name testenv --all
```

--all用于指定删除该环境下的所有软件包，该命令在删除该环境下所有软件包后会删除该环境



### 安装软件包

例

```powershell
conda install requests
```



### 删除软件包

例

```powershell
conda remove --name testenv requests
```

通过--name指定环境，并在其后指定要删除的软件包名



### 导出一个环境下的所有软件包

例

```powershell
conda list --explicit > ./test
```

- conda list --explicit输出当前环境软件包的详细信息
- “>“ 通过重定向将信息输出至test文件



### 通过文件清单安装软件包

本方法可以通过上一个命令导出的清单文件在新的环境中安装其中的软件包

例

```powershell
conda install --file ./test
```

--file 指定从一个文件读取软件包列表
