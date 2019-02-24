## ماهي فائدة الـ model الذي قمنا بعمله (Post) ?

فائدته أننا سنقوم بتمريره من خلال الـ view إلى الـ template وهو مثل العقد (contract) بينهما الاثنين.

بحيث لدينا في كل عنصر post البيانات التالية:

1. صورة كاتب المنشور photo_url
2. اسم كاتب المنشور name
3. المنشور body

يعرف هذا النمط بـ MVT - Model View Template, بحيث لدينا نموذج ودالة تستقبل الطلبات وصفحة لعرض البيانات.

## عرفنا كيفية تمرير البيانات ديناميكياً من الـ View إلى الـ Template

قمنا سابقاً بعمل صفحة المنشورات الرئيسية حسب الـ wireframe الذي قمنا بعمله.

بقي الآن أن نقوم بربط ملف store.py الذي يحتوي على مستودع المنشورات مع مشروع flask, بهذا الشكل:

```python
from flask import Flask, render_template
from store import Post, PostStore

app = Flask(__name__)

dummy_posts = [
    Post(id=1,
         photo_url='https://images.pexels.com/photos/415829/pexels-photo-415829.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=50&w=50', 
         name='Sara', 
         body='Lorem Ipsum'),
    Post(id=2,
         photo_url='https://images.pexels.com/photos/736716/pexels-photo-736716.jpeg?auto=compress&cs=tinysrgb&dpr=1&h=100&w=100', 
         name='John', 
         body='Lorem Ipsum'),
]
post_store = PostStore()
post_store.add(dummy_posts[0])
post_store.add(dummy_posts[1])
```

** لا تنسى نسخ ملف store.py إلى مجلد المشروع **

ثم بإمكانك تمرير المنشورات على دالة render_template في متغير بهذا الشكل:

```python
posts=post_store.get_all()
```

## كيف يمكنني الوصول إلى بيانات المنشورات ؟

بنفس الطريقة التي شاهدتها في الدرس السابق (المرور على بيانات list), ستقوم بالمرور على قائمة posts.

مثال على عرض صور كاتبي المنشورات:

```
{% for post in posts %}
<img src="{{post.photo_url}}">
{% endfor %}
```


## ماهي المهمة المطلوبة ؟

قم بإظهار المنشورات بشكل ديناميكي باستعمال ملف index.html الذي قمت بعمله وملف store.py.

## كيف تقوم بمشاركة الحلول ؟

بإمكانك مشاركة الحلول في مجتمع كورتابز على هذا الرابط:

<a href="https://forums.coretabs.net/t/مشاركة-حلول-تجنب-النسخ-واللصق-باسخدام-الدوال/1159" style="display: block; width: 200px; background-color: #5355e8; background-image:linear-gradient(to left, #2d43e7, #9042e8); color:#fff; padding: 10px; margin: 30px auto; border-radius:100px; text-decoration: none; font-size: 18px; text-align: center;">مشاركة الحل</a>