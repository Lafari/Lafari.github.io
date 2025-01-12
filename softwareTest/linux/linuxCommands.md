# Linux 命令大全

## 系统信息查看命令

### 查看系统版本和内核信息

- `uname -a`
  - **功能**：显示系统的详细信息，包括内核版本、主机名、操作系统类型等。
  - **常用选项**：
    - 无选项：显示所有系统信息。
  - **示例**：
    ```bash
    uname -a
    ```
    **输出示例**：
    ```plaintext
    Linux myhost 5.15.0-58-generic #64-Ubuntu SMP Fri Jan 6 10:00:00 UTC 2025 x86_64 GNU/Linux
    ```

- `cat /etc/os-release`
  - **功能**：查看操作系统的发行版信息，如名称、版本号等。
  - **示例**：
    ```bash
    cat /etc/os-release
    ```
    **输出示例**：
    ```plaintext
    NAME="Ubuntu"
    VERSION="22.04.3 LTS (Jammy Jellyfish)"
    ID=ubuntu
    ```

- `hostname`
  - **功能**：显示或设置系统的主机名。
  - **示例**：
    ```bash
    hostname
    ```
    **输出示例**：
    ```plaintext
    myhost
    ```

### 查看系统运行时间

- `uptime`
  - **功能**：显示系统已运行的时间、当前时间、已登录用户数，以及负载均值。
  - **常用选项**：
    - 无选项：直接显示默认信息。
  - **示例**：
    ```bash
    uptime
    ```
    **输出示例**：
    ```plaintext
    14:35:22 up 7 days,  3:45,  3 users,  load average: 0.05, 0.03, 0.00
    ```

### 查看当前登录用户

- `who`
  - **功能**：显示当前登录系统的用户信息。
  - **示例**：
    ```bash
    who
    ```
    **输出示例**：
    ```plaintext
    user1    tty7         2025-01-12 10:23 (:0)
    user2    pts/0        2025-01-12 14:10 (192.168.1.100)
    ```

- `w`
  - **功能**：显示登录用户的信息及其当前执行的命令。
  - **示例**：
    ```bash
    w
    ```
    **输出示例**：
    ```plaintext
     14:40:45 up 7 days,  3:50,  3 users,  load average: 0.08, 0.04, 0.00
    USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
    user1    tty7     :0               10:23    5:17m  0.30s  0.30s /usr/libexec/gdm-x-session
    user2    pts/0    192.168.1.100   14:10    1.00s  0.01s  0.01s bash
    ```

---

## 文件与目录操作命令

### 显示目录内容

- `ls`
  - **功能**：列出指定目录的内容。
  - **常用选项**：
    - `-l`：显示详细信息（权限、所有者、大小、修改时间）。
    - `-a`：包括隐藏文件（以`.`开头的文件）。
    - `--color`：为不同类型的文件添加颜色（大多数系统默认开启）。
    - `-h`：文件大小以人类可读格式显示（如 KB、MB）。
    - `-t`：按照修改时间排序。
  - **示例**：
    ```bash
    ls -lah --color
    ```
    **输出示例**：
    ```plaintext
    drwxr-xr-x  3 user group 4.0K Jan 12 14:40 .
    drwxr-xr-x 15 user group 4.0K Jan 12 10:23 ..
    -rw-r--r--  1 user group  500 Jan 12 12:00 file.txt
    ```

### 更改当前目录

- `cd`
  - **功能**：切换到指定目录。
  - **常用用法**：
    - `cd /absolute/path`：切换到绝对路径。
    - `cd relative/path`：切换到相对路径。
    - `cd ..`：返回到上一级目录。
    - `cd ~` 或 `cd`：切换到当前用户的主目录。
  - **示例**：
    ```bash
    cd /home/user/documents
    cd ../
    ```

### 创建和删除目录

- `mkdir`
  - **功能**：创建新目录。
  - **常用选项**：
    - `-p`：递归创建父目录（如果不存在）。
  - **示例**：
    ```bash
    mkdir new_folder
    mkdir -p /path/to/new_folder
    ```

- `rmdir`
  - **功能**：删除空目录。
  - **注意**：目录必须为空，否则无法删除。
  - **示例**：
    ```bash
    rmdir empty_folder
    ```

---

### 文件操作命令（扩展部分）

- `cp`
  - **功能**：复制文件或目录。
  - **常用选项**：
    - `-r`：递归复制整个目录。
    - `-v`：显示复制的过程。
    - `-p`：保留文件的属性（如时间戳、权限）。
  - **示例**：
    ```bash
    cp file1.txt file2.txt
    cp -rp source_folder/ destination_folder/
    ```

- `mv`
  - **功能**：移动文件或重命名文件。
  - **常用选项**：
    - `-v`：显示移动或重命名的过程。
  - **示例**：
    ```bash
    mv old_name.txt new_name.txt
    mv file.txt /target/directory/
    ```

- `rm`
  - **功能**：删除文件或目录。
  - **常用选项**：
    - `-r`：递归删除目录及其内容。
    - `-f`：强制删除（不提示）。
  - **示例**：
    ```bash
    rm file.txt
    rm -rf /path/to/directory
    ```

---

## 权限管理命令

### 更改文件权限

- `chmod`
  - **功能**：修改文件或目录的权限。
  - **常用选项**：
    - `-R`：递归修改目录及其内容权限。
  - **权限表示**：
    - 数字形式（如 `755`，表示所有者可读写执行，组和其他用户只读执行）。
    - 符号形式（如 `u+r` 表示给文件所有者增加读权限）。
  - **示例**：
    ```bash
    chmod 755 file.txt
    chmod -R 644 /path/to/directory
    ```

### 更改文件所有者

- `chown`
  - **功能**：修改文件或目录的所有者或所属组。
  - **常用选项**：
    - `-R`：递归修改目录及其内容。
  - **格式**：
    - `chown [owner][:group] file`。
  - **示例**：
    ```bash
    chown user file.txt
    chown user:group file.txt
    ```

### 查看文件权限

- `ls -l`
  - **功能**：以详细列表形式查看文件权限。
  - **示例**：
    ```bash
    ls -l
    ```
    **输出示例**：
    ```plaintext
    -rw-r--r--  1 user group  500 Jan 12 12:00 file.txt
    ```

---

## 网络命令

### 检查网络连接

- `ping`
  - **功能**：测试主机与目标地址之间的网络连通性。
  - **示例**：
    ```bash
    ping -c 4 google.com
    ```

### 显示网络接口信息

- `ifconfig`（旧）或 `ip addr`（新）
  - **功能**：查看或配置网络接口。
  - **示例**：
    ```bash
    ip addr
    ```

### 查看端口占用

- `netstat` 或 `ss`
  - **功能**：显示网络连接、监听端口等信息。
  - **示例**：
    ```bash
    ss -tuln
    ```

---

## 进程管理命令

### 查看进程

- `ps`
  - **功能**：显示当前运行的进程。
  - **常用选项**：
    - `aux`：显示所有用户的所有进程。
  - **示例**：
    ```bash
    ps aux
    ```

### 杀死进程

- `kill`
  - **功能**：通过 PID 杀死指定进程。
  - **示例**：
    ```bash
    kill 1234
    ```

- `killall`
  - **功能**：通过进程名称杀死所有匹配的进程。
  - **示例**：
    ```bash
    killall firefox
    ```

---

## 压缩解压命令

### 打包压缩

- `tar`
  - **功能**：创建或提取归档文件。
  - **常用选项**：
    - `-c`：创建归档。
    - `-x`：提取归档。
    - `-z`：通过 gzip 压缩或解压缩。
    - `-v`：显示详细信息。
    - `-f`：指定文件名。
  - **示例**：
    ```bash
    tar -czvf archive.tar.gz /path/to/directory
    tar -xzvf archive.tar.gz
    ```

### 压缩和解压缩文件

- `gzip` 和 `gunzip`
  - **功能**：压缩和解压缩文件。
  - **示例**：
    ```bash
    gzip file.txt
    gunzip file.txt.gz
    ```

- `zip` 和 `unzip`
