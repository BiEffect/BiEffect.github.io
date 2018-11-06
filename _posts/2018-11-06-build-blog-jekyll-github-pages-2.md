---
layout: post
title: ساخت وبلاگ با گیت هاب و جکیل - بخش دوم
tags: آموزشی
Date: 2018-11-06 19:00
---

سلام با بخش دوم آموزش ساخت وبلاگ در خدمتتون هستم. بخش اول آموزش رو میتونین از [اینجا]( https://bieffect.github.io/2018/10/29/build-blog-jekyll-github-pages.html) مطالعه کنین

اول از همه در پوشه روت یا همون پوشه اصلی وبلاگ پوشه جدیدی به اسم `layout_` بسازین سپس داخل این پوشه فایلی بنام `defualt.html` ایجاد کنید

داخل فایل ساخته شده محتویات زیر رو وارد کنین :

    <!DOCTYPE html>
    <html lang="{{ page.lang | default: site.lang | default: "fa-IR" }}">
    <head>
      {%- include head.html -%}
    </head>
    <body>

      {%- include header.html -%}

    <main class="page-content" aria-label="Content">
          <div dir="rtl" class="wrapper">
            {{ content }}
          </div>
    </main>

    {%- include footer.html -%}

    </body>

    </html>

پس از ذخیره داخل همین پوشه فایل جدیدی به اسم `home.html` میسازیم و خط های زیر رو داخلش وارد و ذخیره میکنیم :

    ---
    layout: default
    ---

    <div class="home">
 
    {%- if page.title -%} 

    <h1 class="page-heading">{{ page.title }}</h1> 

    {%- endif -%}

    {% include google-search.html %}

    {{ content }} 

    {%- if site.posts.size > 0 -%} 

    <h2 class="post-list-heading">

    {{ page.list_title | default: "Posts" }}

    </h2> 

    <ul class="post-list"> 

    {%- for post in site.posts -%} 
    <li>
    {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%} 

    <span class="post-meta">
  
     {{ post.date | date: date_format }}

     </span>

     <h3>
     <a class="post-link" href="{{ post.url | relative_url }}">

     {{ post.title | escape }} 

    </a> 

    </h3>

    {%- if site.show_excerpts -%} 

    {{ post.excerpt }} 

    {%- endif -%} 

    </li>

    {%- endfor -%}

    </ul>

    {%- endif -%}

    </div>

خب فایل بعدی که باید در اینجا ساخته بشه `page.html` هستش :

	---
    layout: default
    ---
    <article class="post"> 

    <header class="post-header"> 

    <h1 class="post-title">

    {{ page.title | escape }}

    </h1> 

    </header>

    <div class="post-content"> 

    {{ content }} 

    </div>

    </article>

و در آخر هم `post.html` :

	---
    layout: default
    ---
    <article class="post h-entry" itemscope itemtype="http://schema.org/BlogPosting"> 

    <header class="post-header"> 

    <h1 class="post-title p-name" itemprop="name headline">

    {{ page.title | escape }}

    </h1> 

    <p class="post-meta"> 

    <time class="dt-published" datetime="{{ page.date | date_to_xmlschema }}" itemprop="datePublished"> 

    {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%} 

    {{ page.date | date: date_format }} 

    </time>

    {%- if page.author -%} • 

    <span itemprop="author" itemscope itemtype="http://schema.org/Person">

    <span class="p-author h-card" itemprop="name">

    {{ page.author }}

    </span>

    </span>

    {%- endif -%}

    </p>

    </header>

    <div class="post-content e-content" itemprop="articleBody"> 

    {{ content }} 

    </div>

    <span>

    {% for tag in page.tags %} 

    {% capture tag_name %}

    {{ tag }}

    {% endcapture %}

    <a href="/tag/{{ tag_name }}"><code class="highligher-rouge"><nobr> {{ tag_name }}</nobr></code>&nbsp;</a> 

    {% endfor %} 

    </span>

    {%- include disqus_comments.html -%} 

    <a class="u-url" href="{{ page.url | relative_url }}" hidden> </a>

    </article>


#### کامنت

حالا نوبت به گذاشتن کامنت برای پست ها میرسه ما برای اینکار از **disqus** استفاده میکنیم که متاسفانه فیلتره و برای ثبت نام ف.یلترشکن نیاز دارین که البته این ماجرا در مورد افرادی که میخوان براتون کامنت بزارن هم صدق میکنه

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

حالا دوباره به پوشه اصلی وبلاگ روی سیستممون میریم و پوشه جدیدی به نام `includes_` میسازیم

داخل این پوشه فایلی به نام `disqus_comments.html` بسازین و کدی رو که از disqus گرفته بودین واردش کنین

در انتها وارد فایل `config.yml_` بشین و خط زیر رو واردش کنید :

	 disqus_shortname: bieffect-github-io

اسم من به این شکله شما اسم خودتونو وارد کنین 

در انتها این نکته رو اشاره کنم که خوبه این خطوط داخل فایل `config.yml_` باشه :

    title: Your site title

    email: Your email

    author: Ali Moghaddas #example

    url: https://bieffect.github.io #example
    
    lang: fa_IR

    timezone: Asia/Tehran 

    comment_system: disqus

    disqus_shortname: bieffect-github-io 

    theme: minima 

    plugins: 
      - jekyll-feed
      - jekyll-seo-tag
      - jekyll-sitemap
  

خب به پایان این قسمت آموزش رسیدیم امیدوارم مشکلی نداشته باشین و اگه مشکلی بود در کامنت ها که فیلتره :) یا ایمیلم که در پایین صفحه موجوده مطرح کنین XO

