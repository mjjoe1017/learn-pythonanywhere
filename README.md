# Django 架設 WEB

先至[pythonanywhere](https://www.pythonanywhere.com)註冊 <br>

建立網站頁面： `點選頁籤Web` > 
`點選Add a new web app` > 
`Next` > 
`Manual configuration` >
`Python 3.7` > 
`Next` > 
`點選username.pythonanywhere.com` <br>

上傳範例： `點選頁籤Files` > `Upload a file` > `上傳mysite.zip檔案` <br>

解壓縮檔案： `點選頁籤Consoles` > `Bash` <br>

在Bash Console 輸入以下指令

> unzip mysite.zip


# 在虛擬環境安裝Django

在Bash Console 輸入以下指令

> virtualenv venv

> source venv/bin/activate

> cd venv

> pip install "django<1.9"

> django-admin startproject mysite

> cd mysite

<br>

# 修改web app設定

WEB

Virtualenv： 點選`Enter path to a virtualenv, if desired` > `輸入/home/yourName/venv` <br>

:star: 注意 :star: 若出現`This virtualenv seems to have the wrong Python version (2.7 instead of 3.7).` 

需要更改Code: `Python version 2.7` > `save`
<br>

# WSGI-Web Server Gateway Interface

> `點選WSGI configuration file: /var/www/yourName_pythonanywhere_com_wsgi.py`

貼上以下程式碼
```
import os
import sys

path = '/home/yourName/mysite'
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler
application = StaticFilesHandler(get_wsgi_application())
```
> `save`


# 修改設定

點選Files > Directories: mysite/mysite/settings.py

> ALLOWED_HOSTS = ['\*']

> LANGUAGE_CODE = 'zh-TW'

> TIME_ZONE = 'Asia/Taipei'

> USE_I18N = True

> USE_L10N = True

> USE_TZ = True 
