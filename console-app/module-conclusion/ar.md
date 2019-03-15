## أصبح لدينا نظام الـ blog جاهز <span style="font-size: 26px;">:confetti_ball:</span>

كل شيء جاهز. لنجرب كيف يعمل النظام قبل الإنتقال على المرحلة التالية, لدينا هذه الأكواد في ملف `store.py`:

```python
class Post:
    def __init__(self, id, photo_url, name, body):
        self.id = id
        self.photo_url = photo_url
        self.name = name
        self.body = body

posts = []

class PostStore:
    def get_all(self):
        # get all posts
        return posts

    def add(self, post):
        # append post
        posts.append(post)

    def get_by_id(self, id):
        # search for post by id
        result = None

        for post in posts:
            if post.id == id:
                result = post
                break

        return result

    def update(self, id, fields):
       # update post data
       instance = self.get_by_id(id)

       instance.photo_url = fields['photo_url']
       instance.name = fields['name']
       instance.body = fields['body']

    def delete(self, id):
        # delete post by id
        instance = self.get_by_id(id)
        posts.remove(instance)
```

## إنشاء منشورات ومستودع لها

بالتأكيد أنت تعرف كيف تقوم بإنشاء objects للكلاس Post

```python
post1 = Post(id=1,
         photo_url='https://images.pexels.com/photos/415829/pexels-photo-415829.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=50&w=50',
         name='Sara',
         body='Lorem Ipsum')
post2 = Post(id=2,
         photo_url='https://images.pexels.com/photos/736716/pexels-photo-736716.jpeg?auto=compress&cs=tinysrgb&dpr=1&h=100&w=100',
         name='John',
         body='Lorem Ipsum')
```

بإمكانك الآن طباعة هذه الـ post objects باستعمال print, مثلاً لطباعة المنشور الأول post1:

```
print(post1)
```

ستظهر لديك نتيجة غريبة مثل:

```
<__main__.Post object at 0x000000131A2EAEF0>
```

تعني أن الـ object هذا يوجد في ذاكرة الجهاز (RAM) على العنوان 0x000000131A2EAEF0, لكن هذا لا يهمنا بالفعل وبإمكاننا طباعة اسم كاتب المنشور باستعمال

```
print(post1.name)
```

سيطبع هذا السطر Sara بالتأكيد.

## إضافة وجلب المنشورات

أول شيء سنحتاج أيضاً مستودع لضم هذه المنشورات إليه

```python
store = PostStore()
```

الآن, نستعمل الدوال get_all و add بهذا الشكل:

```python
store.add(post1)
store.add(post2)
```

الآن تم إضافة المنشور post1 و post2 إلى المستودع (باستعمال القائمة).
ولجلب جميع المنشورات وطباعتها نكتب:

```python
print(store.get_all())
```

وهنا سيطبع لنا قائمة المنشورات (عناوين الـ objects على الذاكرة):

```
[<__main__.Post object at 0x0000006ED0D0AEF0>, <__main__.Post object at 0x0000006ED0D0AF28>]
```

أي أننا الآن نتعامل مع القائمة posts, وممكن أن ندخل على العناصر باستعمال الـ index, مثلاً لطباعة أول منشور في القائمة نضيف `[0]`:

```
print(store.get_all()[0])
```

## جلب منشور عبر الـ id

لطباعة منشور (في حالة معرفتنا ماهو الـ id), نستعمل الدالة get_by_id... مثلاً للوصول للمنشور الذي id خاصته 2 نكتب:

```python
print(store.get_by_id(2))
```

كما هو متوقع سيطبع هذا السطر عنوان هذا الـ object في الذاكرة, مثلاً:

```
<__main__.Post object at 0x000000131A2EAEF0>
```

ولطباعة اسم كاتب المنشور نستعمل

```python
print(store.get_by_id(1).name)
```

## حذف المنشور عبر الـ id

تعمل الدالة delete بنفس الطريقة التي تعمل بها الدالة get_by_id, مثلاً لحذف المنشور الي الـ id خاصته 2:

```python
store.delete(2)
```

## تعديل بيانات المنشور

سنحتاج أولاً لكتابة البيانات الجديدة للمنشور على شكل `key: value`:

```python
updated_fields = {'name': 'Maryam',
                  'photo_url': 'https://images.pexels.com/photos/736716/pexels-photo-736716.jpeg?auto=compress&cs=tinysrgb&dpr=1&h=100&w=100',
                  'body': 'Lorem Ipsum'}
```

بعدها تقوم بتمرير هذا المتغير على الدالة update, مع الـ id... هنا نقوم بتحديث المنشور ذو id رقم 1:

```python
store.update(1, updated_fields)
```

## أصبح كل شيء جاهز... لننتقل على الوحدة التالية !