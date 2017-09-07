# MAC Shell命令
[TOC]

### Gatekeeper(允许从以下位置安装应用)
系统还有一个保护叫做 Gatekeeper，这个是防止第三方应用访问你的隐私信息的。如果你也想关掉在终端里输入:`sudo spctl --master-disable` 即可。激活 GateKeeper的方法也很简单输入:`sudo spctl --master-enable`，还可以通过`csrutil status`来查询 Rootless 保护的状态

### 编码转换(iconv)
 iconv [OPTION...] [-f encoding] [-t encoding] [inputfile ...]
 修改文件编码的命令
 `iconv -c -f UTF8 -t GBK test.csv > test_2.csv`
>查看文件编码的方法：
>用vi打开文件，然后输入`:set fileencoding`

iconv 可以在mac上做成系统服务（Automator）使之更方便实用
详细操作[看这里](https://app.yinxiang.com/shard/s9/nl/679699/132350b6-013a-4cf3-8e16-a2b73cba03e9/)
1. 创建一个服务类型的脚本
2. 创建Shell脚本
“服务”收到选定的，这一项选择“文稿”
位于，这一项选择“Finder.app”
Shell，这一项选择“/bin/bash”
传递输入，这一项选择“作为自变量”
文本框中输入如下代码：

``` bash
for f in "$@"; do
    if [ -f "$f" ]; then
        iconv -s -c -f UTF8 -t GBK "$f" > /tmp/iconv.utf8.gbk.tmp
        mv /tmp/iconv.utf8.gbk.tmp "$f"
    fi
done
```

