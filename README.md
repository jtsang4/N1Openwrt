N1 OpenWrt.

[![lede](https://img.shields.io/badge/github-lede-blue.svg?style=flat&logo=github)](https://github.com/coolsnowwolf/lede)
![GitHub](https://img.shields.io/github/license/mingxiaoyu/N1Openwrt)

# 喜欢的可以给个 star。要自己编译独一无二的可以 fork。如果有人要贝壳云等其他的，可以提 issue。我就加上去。再次感谢各位。

默认自定义防火墙: iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE

~~每三天自动编译一次~~

# 如何使用

1. fork 项目
2. 在 secrets 中创建 RELEASES_TOKEN，一般一次编译要 2~4 小时，所以要创建一个 github 发布用的 token。
3. 点击 Actions -> Workflows -> Run workflow -> Run workflow
4. N1 Multiple Version 多版本编译
5. N1 Single Version 只编译一个版本
6. Update Checker, 上游更新则编译。MULTIPLE_BUILD: true **编译 mini 和 plus 多版本编译** false，**只编译 mini**

---

## 用户名和密码

- User: root
- Password: password
- Default IP: 192.168.32.2

---

## app list:（mini 图不代表最新的）

- UU 网游加速器
- jd-dailybonus
- ssr+
- ServerChan
- unblockmusic
- aria2
- ddns
- samba4
- KMS
- frp
- docker
- cifs(挂载 SMB/CIFS 网络共享文件夹)
- vsftpd
- usb_printer
- zerotier
- flowoffload
- WIFI

![applist](https://github.com/mingxiaoyu/N1Openwrt/blob/master/imgs/mini.jpg?raw=true)

---

# N1 U 盘写入刷 emmc

```
cd      /root
./install-to-emmc.sh
```

如果一直卡在 fdisk 失败那里的解决办法：一是再多试几次，如果还不成功，则需要手动清空分区表然后再重试，具体命令:

```
  dd   if=/dev/zero   of=/dev/mmcblk2  bs=512  count=1  &&  sync
```

升级降级方法统一为：
把 update-amlogic-openwrt.sh 及 img 镜像上传至 /mnt/mmcblk2p4

```
cd    /mnt/mmcblk2p4
chmod   755  update-amlogic-openwrt.sh
./update-amlogic-openwrt.sh    xxxxx.img
```

---

# + 版和 +o 版的区别

- [[N1 盒子] 关于 N1 直刷包 29+版及 29+o 版的简单说明和不完全测试](https://www.right.com.cn/forum/thread-3190663-1-1.html)
- [[N1 盒子] 终于找到真正的锅了：关于 N1 进行 speedtest 测速忽快忽慢的原因](https://www.right.com.cn/forum/thread-4017145-1-1.html)

根据实际体验，建议刷 + 版而不是 +o 版更加简单易用

---

# 感激

[P3TERX](https://github.com/P3TERX/Actions-OpenWrt)提供的脚本参考

## 云编译的规格

https://docs.github.com/en/actions/reference/virtual-environments-for-github-hosted-runners#supported-runners-and-hardware-resources
