## كل منشور لديه id

الـ id هو **رقم مميز** غالباً يتم إنشاءه في قواعد البيانات, لكن بما أننا نستعمل list فنحن نقوم بعمل رقم يتم زيادته كل مرة بمقدار واحد.

بإمكاننا الإستفادة من الـ id عند القيام بحذف منشور معين, مثلاً لحذف المنشور الذي لديه الـ id رقم 1 ندخل على الصفحة:

```
http://127.0.0.1:5000/posts/delete/1
```

ولكن سنحتاج لعمل route يستقبل هذا الطلب بهذا الشكل:

```python
@app.route('/posts/delete/<int:id>')
def post_delete(id):
```

وأيضاً عند عرض المنشورات على صفحة html, يجب إضافة رابط الحذف لكل منشور هكذا:

```python
<a href="{{ url_for('post_delete', id=post.id) }}">Delete</a>
```

## ماهي المهمة المطلوبة ؟

قم بإضافة آلية حذف منشور على موقعك.

## كيف تقوم بمشاركة الحلول ؟

قم بتحديث المستودع خاصتك على github, وشاركنا رابط المشروع.

بإمكانك مشاركة الحلول في مجتمع كورتابز على هذا الرابط:

<a href="https://forums.coretabs.net/t/مشاركة-حلول-حذف-المنشورات/1365" style="display: block; width: 200px; background-color: #5355e8; background-image:linear-gradient(to left, #2d43e7, #9042e8); color:#fff; padding: 10px; margin: 30px auto; border-radius:100px; text-decoration: none; font-size: 18px; text-align: center;">مشاركة الحل</a>