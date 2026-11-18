# Linux 常用命令

> 实验二 · Linux 常用命令整理与总结

---

## 一、目录与文件操作

| 命令 | 作用 | 示例 |
| --- | --- | --- |
| `pwd` | 显示当前所在目录的绝对路径 | `pwd` |
| `ls` | 列出目录内容 | `ls -lh` 以易读方式显示详细信息 |
| `cd` | 切换目录 | `cd /etc`、`cd ~`、`cd ..` |
| `mkdir` | 创建目录 | `mkdir -p test/a/b` 递归创建多级目录 |
| `rmdir` | 删除空目录 | `rmdir test` |
| `touch` | 创建空文件 / 更新时间戳 | `touch hello.txt` |
| `cp` | 复制文件或目录 | `cp -r dir1 dir2` 递归复制目录 |
| `mv` | 移动或重命名 | `mv a.txt b.txt` |
| `rm` | 删除文件或目录 | `rm -rf test` 强制递归删除（慎用） |
| `ln` | 创建链接 | `ln -s /usr/bin/python3 py` 创建软链接 |
| `tree` | 树形显示目录结构 | `tree -L 2` |
| `find` | 按条件查找文件 | `find . -name "*.md"` |

---

## 二、文件内容查看与处理

| 命令 | 作用 | 示例 |
| --- | --- | --- |
| `cat` | 一次性输出全部内容 | `cat hello.txt` |
| `more` / `less` | 分页查看文件 | `less /etc/passwd`（`q` 退出） |
| `head` | 查看文件开头若干行 | `head -n 10 access.log` |
| `tail` | 查看文件末尾若干行 | `tail -f app.log` 实时跟踪日志 |
| `grep` | 按关键字过滤内容 | `grep -n "error" app.log` |
| `wc` | 统计行数、单词数、字节数 | `wc -l hello.txt` |
| `sort` | 排序 | `sort -n num.txt` |
| `uniq` | 去除相邻重复行 | `sort names.txt \| uniq -c` |
| `diff` | 比较两个文件的差异 | `diff a.txt b.txt` |
| `echo` | 输出内容到终端或文件 | `echo "hello" > hello.txt` |

> 输出重定向：`>` 覆盖写入，`>>` 追加写入，`|` 管道把前一个命令的结果交给后一个命令。

---

## 三、权限与用户管理

| 命令 | 作用 | 示例 |
| --- | --- | --- |
| `chmod` | 修改文件权限 | `chmod 755 run.sh`、`chmod +x run.sh` |
| `chown` | 修改文件所有者 | `sudo chown user:user a.txt` |
| `chgrp` | 修改文件所属组 | `chgrp dev a.txt` |
| `whoami` | 查看当前用户名 | `whoami` |
| `id` | 查看用户 UID、GID 和所属组 | `id` |
| `passwd` | 修改用户密码 | `passwd` |
| `su` | 切换用户 | `su - root` |
| `sudo` | 以管理员权限执行命令 | `sudo apt update` |
| `useradd` / `userdel` | 添加 / 删除用户 | `sudo useradd tom` |

> 权限数字含义：`r=4`、`w=2`、`x=1`，`755` 即属主可读写执行、同组和其他用户可读执行。

---

## 四、进程与系统状态

| 命令 | 作用 | 示例 |
| --- | --- | --- |
| `ps` | 查看进程 | `ps aux`、`ps -ef` |
| `top` / `htop` | 动态查看 CPU、内存占用 | `top` |
| `kill` | 结束指定 PID 的进程 | `kill -9 1234` |
| `killall` | 按名称结束进程 | `killall firefox` |
| `df` | 查看磁盘空间使用情况 | `df -h` |
| `du` | 统计目录占用空间 | `du -sh *` |
| `free` | 查看内存使用情况 | `free -h` |
| `uname` | 查看系统信息 | `uname -a` |
| `date` | 显示或设置时间 | `date "+%Y-%m-%d %H:%M:%S"` |
| `uptime` | 查看开机时长与负载 | `uptime` |
| `history` | 查看历史命令 | `history \| tail -20` |
| `clear` | 清屏 | `clear` 或 `Ctrl + L` |
| `shutdown` / `reboot` | 关机 / 重启 | `sudo shutdown -h now`、`sudo reboot` |

---

## 五、压缩与解压

| 命令 | 作用 | 示例 |
| --- | --- | --- |
| `tar` | 打包 / 解包 | 打包：`tar -czvf a.tar.gz dir`；解压：`tar -xzvf a.tar.gz` |
| `gzip` / `gunzip` | 压缩 / 解压 .gz 文件 | `gzip a.txt`、`gunzip a.txt.gz` |
| `zip` / `unzip` | 压缩 / 解压 .zip 文件 | `zip -r a.zip dir`、`unzip a.zip` |

> 参数记忆：`c` 创建、`x` 解压、`z` 使用 gzip、`v` 显示过程、`f` 指定文件名。

---

## 六、网络与远程操作

| 命令 | 作用 | 示例 |
| --- | --- | --- |
| `ping` | 测试网络连通性 | `ping -c 4 www.baidu.com` |
| `ip addr` / `ifconfig` | 查看网卡与 IP 地址 | `ip addr` |
| `ss` / `netstat` | 查看端口与连接状态 | `ss -tlnp` |
| `ssh` | 远程登录服务器 | `ssh user@192.168.1.10` |
| `scp` | 远程传输文件 | `scp a.txt user@ip:/home/user/` |
| `wget` | 下载文件 | `wget https://example.com/a.zip` |
| `curl` | 发起 HTTP 请求 | `curl -I https://www.baidu.com` |
| `hostname` | 查看主机名 | `hostname -I` |

---

## 七、软件包管理

| 系统 | 命令 | 作用 |
| --- | --- | --- |
| Ubuntu / Debian | `sudo apt update` | 更新软件源列表 |
| Ubuntu / Debian | `sudo apt install vim` | 安装软件 |
| Ubuntu / Debian | `sudo apt remove vim` | 卸载软件 |
| Ubuntu / Debian | `dpkg -l` | 列出已安装的软件包 |
| CentOS / RHEL | `sudo yum install vim` | 安装软件 |
| CentOS / RHEL | `sudo dnf update` | 更新系统软件 |

---

## 八、Vim 编辑器常用操作

| 操作 | 说明 |
| --- | --- |
| `vim 文件名` | 打开或新建文件 |
| `i` / `a` / `o` | 进入插入模式（当前位置 / 后一位 / 下一行） |
| `Esc` | 回到命令模式 |
| `:w` | 保存 |
| `:q` | 退出 |
| `:wq` 或 `ZZ` | 保存并退出 |
| `:q!` | 强制退出不保存 |
| `dd` / `yy` / `p` | 删除整行 / 复制整行 / 粘贴 |
| `/关键字`、`n` | 查找关键字并跳到下一处 |
| `gg` / `G` | 跳到文件首行 / 末行 |

---

## 九、常用命令组合示例

```bash
# 1. 查看占用空间最大的 5 个目录
du -sh * | sort -rh | head -n 5

# 2. 统计当前目录下 .md 文件的个数
find . -name "*.md" | wc -l

# 3. 实时查看日志中的错误信息
tail -f app.log | grep "ERROR"

# 4. 给目录下所有 .sh 脚本添加可执行权限
chmod +x *.sh

# 5. 打包并压缩整个项目目录
tar -czvf project.tar.gz project/
```

---

## 十、实验小结

1. 掌握了目录与文件的创建、复制、移动、删除等基本操作。
2. 学会了使用 `cat`、`less`、`grep`、`head`、`tail` 查看和过滤文件内容。
3. 理解了 Linux 的权限模型，能够使用 `chmod`、`chown` 管理文件权限。
4. 能够使用 `ps`、`top`、`kill` 等命令查看和管理进程。
5. 熟悉了 `tar`、`ssh`、`scp` 等压缩与远程操作命令，为后续实验打下基础。
