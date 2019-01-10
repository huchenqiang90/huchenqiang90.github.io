# huchenqiang90.github.io
TeamCity mac os 安装流程
1. 从jetbrain官网下载解压teamcity
2. 放到～/Documents/TeamCity  目录下（目录自定义）
3. 首次启动流程

```
cd TeamCity/bin/runAll

sh runAll.sh start
In your browser,
//打开这个地址，就可以看到服务已经启动
http://localhost:8111/
```
4.将TeamCity设置为随机自启动，创建
/Library/LaunchDaemons/jetbrains.teamcity.server.plist 
，重启之后就可以看到TeamCity已经能够启动成功，注意修改WorkingDirectory路径

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>WorkingDirectory</key>
<string>～/Documents/TeamCity</string>
<key>Debug</key>
<false/>
<key>Label</key>
<string>jetbrains.teamcity.server</string>
<key>OnDemand</key>
<false/>
<key>KeepAlive</key>
<true/>
<key>ProgramArguments</key>
<array>
<string>/bin/bash</string>
<string>--login</string>
<string>-c</string>
<string>bin/teamcity-server.sh run</string>
</array>
<key>RunAtLoad</key>
<true/>
<key>StandardErrorPath</key>
<string>logs/launchd.err.log</string>
<key>StandardOutPath</key>
<string>logs/launchd.out.log</string>
</dict>
</plist>
```
