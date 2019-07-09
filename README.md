# KeepMyGoogleVoice



KeepMyGoogleVoice是使用Python脚本自动发送短信给cloudflare来实现保活Google Voice。默认情况下，将发送一条短信到`8336721001`查询`cloudflare.com`的IP。如果你想修改，可以在执行完一键脚本后，更改`/root/gv.py`中的`phoneNumber`和`text`内容。

支持的系统版本：Debain 9/Ubuntu 16.04+/CentOS 7（不建议CentOS 7，可能存在兼容性问题。）

任意方法都无法登录Google Voice，尤其是当出现`googlevoice.util.LoginError`类似错误提示，建议前往<https://accounts.google.com/DisplayUnlockCaptcha> 检查是否开启了安全验证，而导致的账号被风控。

执行此脚本后，对于CentOS 7将自动安装python和python-pip；对于Debain 9/Ubuntu 18.04+将自动安装python3和python3-pip。



### 一键脚本如下，安装过程中需要输入google账号和密码。

```
wget --no-check-certificate -O gv.sh https://raw.githubusercontent.com/veip007/KeepMyGoogleVoice/master/gv.sh && chmod +x gv.sh && bash gv.sh
```

完成安装后，手动将你的账号和密码输入到`/root/gv.py`中，具体位置如如下：

```
voice.login(email='xxxxx@gmail.com', passwd='xxxxx')
```





### 仅当一键脚本无法正常使用是才参考此项

如果上述一脚脚本无法执行，可以手动安装。执行以下命令，手动输入Google账号和密码，并通过crontab将其设置为每月执行一次。

```
wget --no-check-certificate -O gv.py https://raw.githubusercontent.com/veip007/KeepMyGoogleVoice/master/gv.py && chmod +x gv.py
```

并且，对于CentOS 7 执行以下命令
```
yum -y install epel-release
yum -y install python36
yum -y install python36-setuptools
easy_install-3.6 pip
pip3 install googlevoice
python3 gv.py
```

对于Debian 9/Ubuntu 16.04+ 执行以下命令
```
apt install python3
apt install python3-pip
pip3 install googlevoice
python3 gv.py
```
#### 多用户创建:
gv1.py gv2.py gv3.py 类推，然后配合crontab 每月一次即可

