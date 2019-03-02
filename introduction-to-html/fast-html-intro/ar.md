## لغة HTML هي لغة توصيف markup, وليست لغة برمجة !

تستعمل HTML بشكل أساسي في عمل **Static Pages** (صفحات ستاتيكية - صفحات ثابتة), لا تقوم بعمليات حسابية مثل بايثون, لأنها ليست لغة برمجة.

أي أنه لا يمكنك تغيير بيانات الصفحة عند تشغيلها, **كما هي مكتوبة ستظهر في المتصفح**.

## التقسيم الصحيح للصفحة باستعمال العناصر الدلالية Semantic Elements

بدلاً من استعمال div لتقسيم الصفحة بشكل متواصل, يجدر الإشارة إلى أن الطريقة الأصح لتقسيم الصفحة هي باستعمال العناصر الدلالية Semantic Elements كونها تعطي العناصر معنى أوضح.

فمثلاً عند عمل الجزء العلوي من الصفحة نستعمل الوسم **header** بهذا الشكل:

```html
<header>
    <h1>Posty</h1>
    <nav>
        <a href="post-add.html">New</a>
    </nav>
</header>
```

ونفس الأمر بالنسبة لجزء الكروت, نستعمل **main** لجمع كل الكروت, و **article** لكل كرت:

```html
<main>

    <article>
        <div>
            <img src="https://images.pexels.com/photos/415829/pexels-photo-415829.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=50&w=50">
        </div>
        <div>
            <h2>Yasser Alnajjar</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Inventore repellendus itaque rem 
                reprehenderit tempora officia sapiente? Hic, quae qui atque, quaerat, vitae distinctio 
                similique facilis iste nostrum?</p>
            <div>
                <a href="edit">Edit</a> |
                <a href="delete">Delete</a>
            </div>
        </div>

    </article>

    <article>
        <div>
            <img src="https://images.pexels.com/photos/736716/pexels-photo-736716.jpeg?auto=compress&cs=tinysrgb&dpr=1&h=100&w=100">
        </div>
        <div>
            <h2>Mohammed Alhakem</h2>
            <p>Quae qui atque, quaerat, vitae distinctio libero quas similique facilis iste nostrum?</p>
            <div>
                <a href="edit">Edit</a> |
                <a href="delete">Delete</a>
            </div>
        </div>
    </article>


</main>
```