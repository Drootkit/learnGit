# learnGit

该仓库用来测试如何一台设备通过config文件配置多个github账号用于提交
本地拥有两个rsa密钥，对应一个hexo博客的github和这个gitbook账号的github，在平时提交的时候会出现权限错误，于是就尝试利用config来解决。
测试证明这是可以的。
## 配置
```
# github drotkit
Host drootkit.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile C:\\Users\\rootkit\\.ssh\\id_rsa2

# github hellorootkit
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile C:\\Users\\rootkit\\.ssh\\id_rsa
```
如上配置即可，这里需要注意 `HostName`一定要是github，这是不可以随便定义的，但是`Host`是需要改成自己的样子用来区分的。

## 测试
随便一个目录，执行如下命令
```
git init
git add testfile
git commit -m "test_config"
git push -f git@drootkit.com:Drootkit/learnGit.git
```
最后一步加-f是直接强制覆盖，因为我事先没有clone
