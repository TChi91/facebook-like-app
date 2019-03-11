## مالذي قمنا بعمله ؟

قمنا بكتابة الأسطر:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/index')
def home():
    return 'Hi there'

app.run()
```

والتي تعني:

> قم باستقبال الطلبات (requests) على الرابط `/index` ولكن من النوع GET

## ماهو طلب GET (أو ما يعرف به GET request) ؟

يوجد لدينا أنواع كثيرة من الطلبات تعرف بـ HTTP Verbs (أفعال HTTP).

إحدى هذه الأنواع هي GET, والتي تعني "**اجلب**"... من اسمها.

يوجد طلبات أخرى مثل **POST لإنشاء** عنصر, أو **DELETE لحذف** عنصر, سنتعرف عليها مستقبلاً :wink:

## هممم... ولكن, كيف عرف flask أننا نريد GET ؟

بطبيعة الحال, flask تقوم بإضافة البارامتر `methods = ['GET']` والذي يقوم باستقبال طلبات GET... أي أنك حينما تكتب:

```python
@app.route('/index')
def home():
    return 'Hi there'
```

ستقوم فلاسك بترجمتها إلى:

```python
@app.route('/index', methods = ['GET'])
def home():
    return 'Hi there'
```

## ماهو المهم أن تعرفه ؟

المهم أن تعرفه أن المتصفح يقوم بالطلبات باستعمال HTTP Verb ورابط URL بهذا الشكل:

```
GET /index
```