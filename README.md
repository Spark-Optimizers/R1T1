<p align="center">
  <a href="" rel="noopener">
 <img src="http://optimizer.math.sharif.edu/wp-content/uploads/2021/02/optimizer.png" alt="Optimizer logo"></a>
</p>
<h3 align="center">تیم اسپارک</h3>

<div align="center">

  [![Status](https://img.shields.io/badge/status-active-success.svg)]() 
  [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/mtefagh/demos/HEAD)
  [![License](https://img.shields.io/badge/license-GPL-blue.svg)](https://github.com/mtefagh/demos/blob/master/LICENSE)

</div>

---

<p align="center"> معرفی و توضیح مختصر روش استفاده شده و در صورت تمایل بج‌هایی که علاقه‌مند هستید را به جای بج‌های بالا جایگزین کنید
    <br> 
</p>

## 📝 فهرست مطالب
- [صورت‌بندی سوال](#problem_statement)
- [الگوریتم بهینه‌سازی](#idea)
- [محدودیت‌ها](#limitations)
- [ایده‌های گسترش](#future_scope)
- [روند اجرا](#getting_started)
- [نحوه استفاده](#usage)
- [وابستگی‌ها](#tech_stack)
- [نویسندگان](#authors)

## 🧐 صورت‌بندی سوال <a name = "problem_statement"></a>
صورت برنامه‌ریزی :
  
  ```math
  find  v
  s.t.  Sv=0
        l <= v <= u
  ```
برنامه ریزی بالا خطی است زیرا کافیست یک جواب شدنی برای قید های خطی این برنامه ریزی پیدا کنیم. 
پس قید ها را همانگونه که هستند با یک تابع هدف خطی دلخواه (مثلا تابع ثابت) به
<div>JuMP</div>
میدهیم و برای حل آن از یک سالور برنامه ریزی خطی مانند
<div>GLPK</div>
استفاده میکنیم.
  
## 💡 الگوریتم بهینه‌سازی <a name = "idea"></a>
```math
  min  1
  s.t.  Sv=0
        l <= v <= u
  ```
برنامه ریزی بالا را در جومپ پیاده سازی میکنیم.
```
model = Model(GLPK.Optimizer)
@variable(model,v[1:n])
@constraint(model, l .<= v)
@constraint(model, v .<= u)
@constraint(model, S*v .== mzeros)
@objective(model,Min,1)
optimize!(model)
```
و سالور یک جواب شدنی برای این برنامه ریزی می یابد.

## ⛓️ محدودیت‌ها <a name = "limitations"></a>
محدودیتی در این بخش از مسابقه وجود ندارد و با نصب
<div>JuMP</div>
و
<div>GLPK</div>
میتوان یک جواب شدنی برای هر ۳ ورودی مسابقه به دست آورد.


## 🏁 روند اجرا <a name = "getting_started"></a>
در صورتی که در پکیج های
گفته شده در بخش بعدی 
را در جولیا نصب داشته باشید میتوانید فایل نوتبوک مربوط به هر دور مسابقه را
به صورت یکجا یا سلول به سلول اجرا کنید. در انتها یک فایل
<div>output.txt<\div>
در همان مسیر ذخیره میشود که حاوی خروجی آن ورودی از مساله است.

### پیش‌نیازها

  

## 🎈 نحوه استفاده <a name="usage"></a>
با اجرای کامل کد خروجی مساله داده میشود و نیازی به فراخوانی مجزای تابعی نخواهید داشت.

## ⛏️ وابستگی‌ها <a name = "tech_stack"></a>
  برنامه در زبان جولیا نوشته شده و لیست پکیج های مورد نیاز در ادامه آمده است :
```
  MAT
  JuMP
  GLPK
  SparseArrays
  LinearAlgebra
  DelimitedFiles
```

## ✍️ نویسندگان <a name = "authors"></a>
در این بخش ابتدا همه‌ی اعضای گروه به صورت مساله فکر کردند و سپس در یک جلسه‌ی اسکایپ به صورت آنلاین، کد این سوال توسط ایدا افشار محمدیان نوشته شد و متین امینی و ملینا مهرانی ایده های خود را برای پیاده سازی و دیباگ مطرح کردند و نهایتا این ایده روی دیتای آزمایشی، تست شد..
