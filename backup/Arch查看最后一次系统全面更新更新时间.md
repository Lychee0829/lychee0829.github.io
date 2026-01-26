## 在这里可使用命令 `grep -e -Syu /var/log/pacman.log | tail -1` 
具体解释如下：

1. **`grep -e -Syu /var/log/pacman.log`**：
   - `-e`：告诉 `grep` 下一个参数是要搜索的模式。
   - `-Syu`：要匹配的模式（例如，运行过 `pacman -Syu` 的行）。
   - `/var/log/pacman.log`：记录包管理器操作（如系统更新）的日志文件。

2. **`| tail -1`**：
   - 将 `grep` 的输出通过管道传递给 `tail -1`，后者返回结果的**最后一行**。

## 原理
- `pacman` 命令的 `-Syu` 参数用于同步软件包数据库并升级所有系统软件包，相关操作会被记录到 `/var/log/pacman.log`。
- 使用 `grep -e -Syu` 可以筛选出所有执行过完整系统更新（`pacman -Syu`）的记录。
- `tail -1` 能提取出**最近一次**此类更新的日志。

## 输出结果示例
```log
[2025-03-01T14:29:27+0800] [PACMAN] Running 'pacman -Syu'
```

