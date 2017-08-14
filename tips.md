# Tips
- 系统还有一个保护叫做 Gatekeeper，这个是防止第三方应用访问你的隐私信息的。如果你也想关掉在终端里输入:`sudo spctl --master-disable` 即可。激活 GateKeeper的方法也很简单输入:`sudo spctl --master-enable`，还可以通过`csrutil status`来查询 Rootless 保护的状态

