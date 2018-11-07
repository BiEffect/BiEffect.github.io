---
layout: post
title: ساخت وبلاگ با گیت هاب و جکیل - بخش دوم
Date: 2018-11-07 14:00
tags: آموزشی
---
سلام با بخش دوم آموزش ساخت وبلاگ با **گیت هاب** و **جکیل** در خدمتتونم. اگه بخش اول آموزش رو مطالعه نکردین پیشنهاد میکنم از [اینجا](https://bieffect.github.io/2018/10/29/build-blog-jekyll-github-pages.html) دیدن کنین

خب برای شروع در پوشه روت یا همون پوشه اصلیه وبلاگ که قبلا روی کامپیوترتون ساخته بودیم قرار داره پوشه جدیدی به نام `_includes` ایجاد کنین

درون این پوشه فایل جدیدی به نام `head.html` بسازین و محتویات پایین رو داخلش قرار بدین :

    <head> 

     <meta charset="utf-8"> 
     <meta http-equiv="X-UA-Compatible" content="IE=edge"> 
     <meta name="viewport" content="width=device-width, initial-scale=1"> 

     {%- seo -%} 

     <link rel="alternate" type="application/rss+xml" title="My Weblog RSS" href="/feed.xml"> 
     <link rel="stylesheet" href="{{ "/assets/main.css" | relative_url }}"> 

     {%- feed_meta -%}

    </head>

پس از ذخیره در همین پوشه فایل جدیدی به نام `header.html` میسازیم و محتویات زیر رو داخلش قرار میدیم :

    <header class="site-header" role="banner"> 
     <div class="wrapper"> 
      {%- assign default_paths = site.pages | map: "path" -%} 
      {%- assign page_paths = site.header_pages | default: default_paths -%} 
      <a class="site-title" rel="author" href="{{ "/" | relative_url }}">{{ site.title | escape }}</a> 
      {%- if page_paths -%} 
      <nav class="site-nav"> 
      <input type="checkbox" id="nav-trigger" class="nav-trigger" /> 
      <label for="nav-trigger"> 
      <span class="menu-icon"> 
      <svg viewBox="0 0 18 15" width="18px" height="15px"> <path d="M18,1.484c0,0.82-0.665,1.484-1.484,1.484H1.484C0.665,2.969,0,2.304,0,1.484l0,0C0,0.665,0.665,0,1.484,0 h15.032C17.335,0,18,0.665,18,1.484L18,1.484z M18,7.516C18,8.335,17.335,9,16.516,9H1.484C0.665,9,0,8.335,0,7.516l0,0 c0-0.82,0.665-1.484,1.484-1.484h15.032C17.335,6.031,18,6.696,18,7.516L18,7.516z M18,13.516C18,14.335,17.335,15,16.516,15H1.484 C0.665,15,0,14.335,0,13.516l0,0c0-0.82,0.665-1.483,1.484-1.483h15.032C17.335,12.031,18,12.695,18,13.516L18,13.516z"/> </svg> 
      </span> 
      </label> 
     <div class="trigger"> 
      {%- for path in page_paths -%} 
      {%- assign my_page = site.pages | where: "path", path | first -%} 
      {%- if my_page.title -%} 
      <a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a> 
      {%- endif -%} 
      {%- endfor -%} 
     </div> 
      </nav> 
      {%- endif -%} 
     </div>
    </header>

و در انتها فایل جدیدی به اسم `footer.html` میسازیم و محتویات پایین رو داخلش قرار میدیم :

    <footer class="site-footer h-card"> 
     <data class="u-url" href="{{ "/" | relative_url }}"></data> 
      <div class="wrapper"> 
       <h2 class="footer-heading">{{ site.title | escape }}</h2> 
      <div class="footer-col-wrapper"> 
      <div class="footer-col footer-col-1"> 
       <ul class="contact-list"> 
       <li class="p-name"> 
       {%- if site.author -%} 
        {{ site.author | escape }} 
       {%- else -%} 
        {{ site.title | escape }} 
       {%- endif -%} 
      </li> 
       {%- if site.email -%} 
      <li><a class="u-email" href="mailto:{{ site.email }}">{{ site.email }}</a></li> 
       {%- endif -%} 
       </ul> 
      </div> 
      <div class="footer-col footer-col-2"> 
       {%- include social.html -%} 
      </div> 
      <div class="footer-col footer-col-3"> 
       <p>
        {{- site.description | escape -}}
       </p> 
      </div> 
      </div> 
      </div> 
    </footer>

خب فعلا تا اینجا کارمون با پوشه _includes تموم شده. در ادامه داخل پوشه اصلی وبلاگ پوشه جدیدی به نام `_layouts` میسازیم. **از اینجای کار به بعد برای پوشه _layouts از لینک دادن به وبلاگ خودم استفاده میکنم تا پست زیاد طولانی و شلوغ نشه**.

داخل پوشه _layouts فایل جدیدی به نام `defualt.html` میسازیم محتویات [این صفحه](https://github.com/BiEffect/bieffect.github.io/blob/master/_layouts/default.html) رو واردش میکنیم

در ادامه داخل همین پوشه فایل هایی بنام [home.html](https://github.com/BiEffect/bieffect.github.io/blob/master/_layouts/home.html) ، [post.html](https://github.com/BiEffect/bieffect.github.io/blob/master/_layouts/post.html) و [page.html](https://github.com/BiEffect/bieffect.github.io/blob/master/_layouts/page.html) میسازیم. 

**نکته:** تمامی فایل های بالا از خود ریپازیتوری [minima]( https://github.com/jekyll/minima) گرفته شده اما از اونجا که این قالب برای زبان فارسی طراحی نشده یکسری تغییرات داخلش ایجاد کردم که اگه با HTML و CSS کمی آشنایی داشته باشین خودتون میتونین تا این مشکل رو بهبود بدین
پس در ادامه پوشه های
`sass_` و `assets` رو از ریپازیتوری من [دریافت کنین](https://github.com/BiEffect/bieffect.github.io) و داخل پوشه اصلی وبلاگتون قرار بدین

برای راحتی کار میتونین از دستور زیر استفاده کنین تا تمامی فایل ها دانلود بشه :
	
    git clone https://github.com/BiEffect/bieffect.github.io

### اضافه کردن کامنت

حالا نوبت به گذاشتن کامنت برای پست ها میرسه ما برای اینکار از **disqus** استفاده میکنیم که متاسفانه فیلتره و برای ثبت نام ف.یلترشکن نیاز دارین که البته این ماجرا در مورد افرادی که میخوان براتون کامنت بزارن هم صدق میکنه :(

برای شروع در سایت [disqus.com]( https://disqus.com/profile/signup/ ) ثبت نام میکنم

در مرحله بعد روی **I want to install Disqus on my site** کلیک کنین





![disqus_comment_1](/assets/image/disqus_1.jpg) 




سپس اسم سایت و موضوع سایت رو مشخص کنید




![disqus_comment_2](/assets/image/disqus_2.jpg) 




از بین موارد موجود jekyll رو انتخاب کنید




![disqus_comment_3](/assets/image/disqus_3.jpg) 




حالا روی **Universal Embed Code** کلیک و کد داده شده رو جایی ذخیره کنین




![disqus_comment_4](/assets/image/disqus_4.jpg) 




![disqus_comment_5](/assets/image/disqus_5.jpg) 




داخل پوشه `includes_` فایلی به نام `disqus_comments.html` بسازین و کدی رو که از disqus گرفته بودین واردش کنین

در انتها وارد فایل `config.yml_` بشین و خط زیر رو واردش کنید :

	 disqus_shortname: bieffect-github-io

اسم من به این شکله شما اسم خودتونو وارد کنین

در انتها این نکته رو اشاره کنم که این خطوط داخل فایل `config.yml_` باشه :

    title: Your site title

    email: Your email

    author: Ali Moghaddas #example

    url: https://bieffect.github.io #example
    
    lang: fa_IR

    timezone: Asia/Tehran 

    comment_system: disqus

    disqus_shortname: bieffect-github-io #example

    theme: minima 

    plugins: 
      - jekyll-feed
      - jekyll-seo-tag
      - jekyll-sitemap
  

خب به پایان این قسمت آموزش رسیدیم امیدوارم مشکلی نداشته باشین و اگه مشکلی بود در کامنت ها، که فیلتره :) یا ایمیلم که در پایین صفحه موجوده مطرح کنین XO

در ادامه آموزش ها به اضافه کردن تگ، اضافه کردن قابلیت سرچ پستها، اضافه کردن وبلاگ به گوگل سرچ کنسول و… میرسیم
