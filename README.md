[English](README-en.md) ←

# 借助 GitHub Actions 的 OpenWrt 在线集成自动编译.

## [![Build](https://img.shields.io/github/workflow/status/KFERMercer/OpenWrt/OpenWrt-CI/master?)](https://github.com/KFERMercer/OpenWrt/actions?query=workflow%3AOpenWrt-CI) [![Release](https://img.shields.io/github/release/KFERMercer/OpenWrt-CI?color=blue)](https://github.com/KFERMercer/OpenWrt-CI/releases)

支持自动定制固件, 自动调整依赖及生成配置文件, 无需上传配置. 兼容 [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) 以及 OpenWrt trunk.

同时支持自动合并推送上游提交 (也就是自动更新), 直接把`merge-upstream.yml`放入`.github/workflows/`即可 (默认上游为 coolsnowwolf/lede, 高级玩家请自行改写).

感谢[P3TERX](https://github.com/P3TERX/Actions-OpenWrt)珠玉在前.

## 使用教程:

### 在一切开始前, 你需要的是:

- GitHub 账号
- 申请使用 GitHub Actions
- [基本的Git技能](https://www.liaoxuefeng.com/wiki/896043488029600)
- 自己的OpenWrt分支 ([Lean源](https://github.com/coolsnowwolf/lede)或者[官方源](https://github.com/openwrt/openwrt/))
- 脑子

### 相关文章: 作者-糖炒栗子 

- [面向小白的Github_Action使用workflow自动编译lean_openwrt教程](https://zhuanlan.zhihu.com/p/94402324)
- [关于Github Action自动编译Lean_Openwrt的配置修改问题](https://zhuanlan.zhihu.com/p/94527343)

### 1. 注册GitHub账号并开启GitHub Actions (自行搜索方法).

### 2. fork [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) 或者 [OpenWrt trunk](https://github.com/openwrt/openwrt).

### 3. 上传`openwrt-ci.yml`和`merge-upstream.yml`到`/.github/workflows/`下.

### 4. 定制固件:

> 如果你希望定制你的固件:

代码里的注释部分详细介绍了如何在脚本中客制化你的固件. 简单来说, 你只需要解除注释相应行即可.

### 5. 大功告成.

集成编译环境会自动开始编译. 现在返回你的库首页, 点击页面上方的`Actions`按钮就可以查看进度.

> ### 如何下载到编译完成的固件?

进入`Actions`标签页后, 如果相应的集成活动顺利完成 (显示为绿色), 点击页面右上方的`Artifacts`即可看到你的固件 (通常是一个压缩包). 点击即可开始下载.
