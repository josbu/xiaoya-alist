# 115 清理助手

自动清理 115 转存文件。

## Run

```shell
docker run -d \
    --name=xiaoya-115cleaner \
    -v 小雅配置文件目录:/data \
    --net=host \
    -e TZ=Asia/Shanghai \
    --restart=always \
    ddsderek/xiaoya-115cleaner:latest
```

## 清理机制

1. 标准模式，清空 `/最近接收` 下面的文件并同时清理回收站的**对应文件**；24H刷新一次清理文件个数（会员105个，普通5个）；7H运行一次清理。
2. 在小雅配置文件目录下面创建`115_cleaner_only_recyclebin.txt`文件后**只清空**115的回收站，不会清理其他地方的文件；此模式下没有文件个数限制，7H运行一次。
3. 在小雅配置文件目录下面创建`115_cleaner_all_recyclebin.txt`文件后会清空 `/最近接收` 下面的文件并同时**清空**回收站；24H刷新一次清理文件个数（会员105个，普通5个）；7H运行一次清理。
4. 在小雅配置文件目录下面创建`115_cleaner_only_receive.txt`文件后**只清空** `/最近接收` 下面的文件，不会清理其他地方的文件和回收站；24H刷新一次清理文件个数（会员105个，普通5个）；7H运行一次清理。

## ali2115 自动配置

> [!warning]
> 使用此配置在`115 清理助手`后台日志提示配置后需要手动重启小雅容器应用`ali2115.txt`文件的更改！

在小雅配置文件目录下面创建`115_cleaner_auto_set_ali2115.txt`文件后会在`115 清理助手`启动时自动配置`ali2115.txt`文件，此配置之后所有使用`ali2115`转存的文件都将由`115 清理助手`清理。
