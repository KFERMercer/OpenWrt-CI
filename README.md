# 使用 GitHub Actions 的 OpenWrt 在线集成自动编译环境.

## 12月4日更新: (!!自动更新代码!!) 直接把`merge-upstream.yml`放入`.github/workflows/`即可启动自动更新大雕代码.

## 自动定制固件, 自动生成配置文件, 无需上传配置, 依赖自动调整.

## 代码更新即自动编译, 兼容 coolsnowwolf/lede 以及 OpenWrt trunk

感谢[P3TERX](https://github.com/P3TERX/Actions-OpenWrt)珠玉在前.

### 好消息! 好消息!
### 你还在使用别人编译的加料固件吗?!
### 你还在因为学不会Linux命令而苦苦挣扎吗?!
### 你还在用你那双核赛扬装虚拟机吗?!
### 你还在花费半辈子攒下的论坛币只为了下载别人编译好的附件吗?!
### 你还在因为自身原因导致的编译失败而发一些不知所云的issue吗?!
### 生命冇 take two! 我们浪费在编译上的时间已经够多了!
### 21世纪, 自己的才是最好的! 现在人人都可以定制自己的专属固件了! <sub><sub>(不包含三岁及以下儿童)</sub></sub>

---

## 麻瓜级使用教程:

> ### 这个CI脚本和[P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)的同样是云编译, 有什么不同?

这个 CI 脚本可以帮助你在你的 OpenWrt 分支下构建当前库的Op固件, 无需上传配置文件, 不依赖外挂配置脚本, 所以不会污染库文件树, 对Op开发者比较友好.

P3TERX/Actions-OpenWrt 的优势在于, 其可以独立于文件库存在, 可以快速搭建起可用的编译配置, 但是由于 OpenWrt make configure 自身机制的缘故, 生成的配置文件鲁棒性较差, 需要经常重新生成上传配置, 有形中加重了维护负担, 使得使用起来不是很`优雅`.

> ### 这个CI脚本适合哪些人?

- 伸手党 (访问者可以每日下载到当日最新的固件)
- 正在维护自己的 OpenWrt 分支的大佬/初学者/玩家 (可以快速测试自己的代码)
- 没有精力维持一个专用编译机的佛系人士 (梯子到期了?)

> ### 开始吧.

在一切开始前, 你需要的是:

- GitHub 账号
- 申请使用 GitHub Actions
- 自己的OpenWrt分支(fork大雕源或者官方源)
- 识字能力以及基本电脑操作技能
- 脑子

你不需要的是:

- Linux技能
- 对编译失败的处置能力 (脚本由我维护)
- 梯子

### 1. 注册GitHub账号并开启GitHub Actions (自行搜索方法).

### 2. fork [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) 或者[OpenWrt trunk](https://github.com/openwrt/openwrt).

### (coolsnowwolf/lede已经合并此配置, 如果你pork了此库, 请忽略3. 4. 5.步)

### 3. 点击页面上方的`Create new file`按钮, 打开后在文件名处填入`.github/workflows/openwrt-ci.yml`(github 会自动创建路径).

### 4. 打开[这个链接](https://raw.githubusercontent.com/KFERMercer/OpenWrt-CI/master/openwrt-ci.yml), `Ctrl+a`选泽复制页面所有内容黏贴在刚才的下方的大文本框内.

> ### 现在暂停一下, 代码里需要留意一些东西...

如果你只希望生成默认配置, 不经过任何修改的固件, 那你不需要对代码进行任何修改. 自动集成工具会在每次推送后自动编译出最新默认配置的固件.

如果你希望定制你的固件:\
代码里的注释部分详细介绍了如何在脚本中客制化你的固件. 简单来说, 你只需要解除注释相应行即可.

### 正确的定制固件脚本应该是长[这样的](https://github.com/KFERMercer/OpenWrt-by-lean/blob/CI-demo/.github/workflows/openwrt-ci.yml), 此配置基于大雕最新代码, 开启了所有预先写好的定制选项, 同时已经[经过测试](https://github.com/KFERMercer/OpenWrt-by-lean/commit/d31390d3e7b5f178d4e3456d401ded557c207398/checks?check_suite_id=334570354)可用. 悟性再高不如照葫芦画瓢, 如果你的配置一直编译失败, 抄, 请.

现在我们继续:

### 5. 假设你已经完成了脚本修改, 现在点击页面最下方的绿色按钮. 你是色盲也没关系, 因为按钮上写着`Commit new file`.

### 6. 大功告成, 集成编译环境会自动开始编译. 现在返回你的库首页, 点击页面上方的`Actions`按钮就可以查看进度.

> ### 如何下载到编译完成的固件?

进入`Actions`标签页后, 如果相应的集成活动全部完成 (打勾) , 点击页面右上方的`Artifacts`即可看到你的固件 (通常是一个压缩包). 点击压缩包即可开始下载. (别人也可以下载你的固件, 不可思议.)
