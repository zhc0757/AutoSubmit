# 自动打卡

只是为了华工同学方便打卡，不作其他用途。

### SMTP 邮件通知

新增了邮件通知，需要自行填写对应的 SMTP 服务域名，账号密码等。

### 执行环境

- python3
- nodejs

### 使用

在 config 目录下，根据`default.conf`的格式创建一个 conf 文件，并填入对应的数据。

```python
python main.py
```

### 其他

在 linux 上开启定时任务：使用 `crontab -e` 编辑任务

比如我的任务为每天早上 9 点半进行自动打卡

```text
30 9 * * * cd PATH/TO/AUTOSUBMIT/PROJECT/ && python3 main.py >> log_autosubmit 2>&1
```

### 注意

设置任务时需要注意路径。

1. 当出现找不到 node 时，可以在`autopy/autoSubmit.py`文件中，根据自己系统以及 nodejs 的环境修改路径。
2. 在 `crontab -e` 设定任务时的 `cd PATH/TO/AUTOSUBMIT/PROJECT/` 是因为 Python 脚本里用到了相对路径，所以要先改变工作目录。
3. 在 `crontab -e` 设定任务时的 `2>&1` 是为了把错误信息也重定向到日志中，方便出问题时排查。
