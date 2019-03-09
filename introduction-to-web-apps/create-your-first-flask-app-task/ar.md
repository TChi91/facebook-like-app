## استقبال متغيرات في الـ route

بإمكانك استقبال متغيرات تقوم بتمريرها في المتصفح باستعمال:

```python
@app.route('/foo/<x>')
def foo(x):
    return x
```

بإمكانك الآن فتح المتصفح وكتابة الرابط:

```
http://127.0.0.1:5000/foo/hi
```

وسيطبع لك `hi`

## ماهي المهمة المطلوبة

قم بإنشاء مشروع flask جديد

اكتب دالة اسمها say_hello, تقوم باستقبال الطلب هذا:

```
http://127.0.0.1:5000/say-hello/Yaser
```

وتظهر:

```
Hello Yaser
```

لكن في حالة الطلب هذا:

```
http://127.0.0.1:5000/say-hello/mohammed
```

ستظهر:

```
Hello mohammed
```

## كيف تقوم بمشاركة الحلول ؟

قم بتحديث المستودع خاصتك على github, وشاركنا رابط المشروع.

بإمكانك مشاركة الحلول في مجتمع كورتابز على هذا الرابط:

<a href="https://forums.coretabs.net/t/مشاركة-حلول-تجنب-النسخ-واللصق-باسخدام-الدوال/1159" style="display: block; width: 200px; background-color: #5355e8; background-image:linear-gradient(to left, #2d43e7, #9042e8); color:#fff; padding: 10px; margin: 30px auto; border-radius:100px; text-decoration: none; font-size: 18px; text-align: center;">مشاركة الحل</a>