situation & solution https://segmentfault.com/q/1010000008312223


原因就是升级libc.so.6导致的!

GNU中对TZ环境变量的说明中指出，如果TZ没有值，会默认选择时区，具体地址由libc.so.6这个库决定。在升级前，centos的默认时区文件为/etc/localtime。而我新编译的库时，设置了--prefix=/usr/local/glibc-2.14，导致默认路径为变成了/usr/local/glibc-2.14/etc/localtime，自然就找不到默认时区了。

解决方案：

```ln -sf /etc/localtime /usr/local/glibc-2.14/etc/localtime```

done!
