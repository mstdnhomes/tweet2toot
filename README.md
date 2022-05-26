# tweet2toot

A simple script that transport tweets from twitter to Mastodon. Based on the Twitter RSS feed powered by [RSSHub](https://rsshub.app).

```
pip3 install -r requirements.txt
cp conf.sample.ini conf.ini
nano conf.ini
python3 run.py
```
If there is errors when installing the requirements:
```log
error in feedparser setup command: use_2to3 is invalid.
```
That is because feedparser==5.2.1 relies on 2to3  
but 2to3 support has been removed from setuptools since 58.0.0

SO using this:
```python
pip install "setuptools<58"
```

Please install FFmpeg if you need support for twitter's GIFs.

```
sudo apt install ffmpeg

# for Red Hat
# ffmpeg
dnf install https://rpmfind.net/linux/centos/8-stream/PowerTools/aarch64/os/Packages/SDL2-2.0.10-2.el8.aarch64.rpm
dnf install -y https://download1.rpmfusion.org/free/el/rpmfusion-free-release-8.noarch.rpm
dnf -y install ffmpeg
# 验证ffmpeg
ffmpeg -version
```

crontab job setting:
```
crontab -e
```
or (Ubuntu 18.04)
```
nano /etc/crontab
/etc/init.d/cron restart
```

Recommand do job hourly:
```
#m h dom mon dow user  command
13 *    * * *   root    cd /tweet2toot && python3 run.py
```

一个将推特搬运到长毛象的脚本——基于[RSSHub](https://rsshub.app)生成的推特RSS。

推特的开发者账号很长时间没有申请到，所以只能暂时用RSSHub作为数据源了。😢
