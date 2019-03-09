## عملية تحديث منشور مشابهه لعملية إنشاء منشور

نعم, مثلما قرأت بالأعلى... العمليتين مشابهه لبعضها, الفرق الوحيد أن الـ form ستقوم **بملئه مسبقاً** عند الضغط على زر edit.

ستحتاج أولاً إلى إضافة routing:

```
@app.route('/posts/update/<int:id>', methods = ['GET', 'POST'])
def post_update(id):
```

لاحظ أنك هذه المرة ستأخذ الـ id الخاص بالمنشور بمعنى أن زر Edit في الصفحة يحتوي على الرابط:

```
<a href="{{ url_for('post_update', id=post.id) }}">Edit</a> |
```

## كيف يتم ملئ الفورم مسبقاً ؟

عند فتح الصفحة, يجب عليك تمرير البيانات في دالة render_template بهذا الشكل:

```python
elif request.method == 'GET':
    post = post_store.get_by_id(id)
    return render_template('post-update.html', post=post)
```

ولعرض هذه البيانات, ببساطة تستعمل عنصر post للوصول إلى بيانات المنشور, مثال للحصول على رابط الصورة السابق:

```html
<div><input type="text" name="photo_url" value="{{ post.photo_url }}" /></div>
```

## كيف هي عملية تحديث المنشور ؟

لجعل الأمور سهلة عليك, قمنا بإعطائك طريقة أخذ البيانات من الفورم واستخدامها في تحديث المنشور

```python
if request.method == 'POST':
    update_fields = {
        'photo_url': request.form['photo_url'], 
        'name': request.form['name'], 
        'body': request.form['body']
    }
    post_store.update(id, update_fields)

    return redirect(url_for('home'))
```

## ماهي المهمة المطلوبة ؟

قم بإضافة آلية تحديث منشور على موقعك.

## كيف تقوم بمشاركة الحلول ؟

قم بتحديث المستودع خاصتك على github, وشاركنا رابط المشروع.

بإمكانك مشاركة الحلول في مجتمع كورتابز على هذا الرابط:

<a href="https://forums.coretabs.net/t/مشاركة-حلول-تجنب-النسخ-واللصق-باسخدام-الدوال/1159" style="display: block; width: 200px; background-color: #5355e8; background-image:linear-gradient(to left, #2d43e7, #9042e8); color:#fff; padding: 10px; margin: 30px auto; border-radius:100px; text-decoration: none; font-size: 18px; text-align: center;">مشاركة الحل</a>