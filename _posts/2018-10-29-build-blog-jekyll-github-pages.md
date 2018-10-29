---
layout: post
date: 2018-10-29 18:25:00
title: ساخت وبلاگ با گیت هاب و جکیل
---
سلام خیلی خوشحالم که در خدمتتونم 

میخوام امروز ساخت وبلاگ با میزبانی GitHub و [jekyll](https://jekyllrb.com) که یک مولد صفحات ایستاست رو آموزش بدم

لازم به ذکره که در این آموزش من از لینوکس اوبونتو استفاده میکنم

خب بریم سراغ کارمون اصلا سخت نیست ;)

1. برای شروع اگه حساب کاربری در [گیت هاب](/https://github.com) ندارین خیلی راحت یدونه بسازین

2. در مرحله بعد باید یک ریپازیتوری جدید ساخته بشه

![Image](https://www.dropbox.com/s/baexzxy6olhom5z/build_blog01.jpg?dl=0) 

دقت کنین که اسمی که برای ریپازیتوری انتخاب میکنید بصورت زیر باشه :

	 username.github.io


![Image](https://www.dropbox.com/s/koy3y2vr4kk4ydv/build_blog02.jpg?dl=0) 

3. برای کنترل وبلاگ از طریق کامپیوتر شخصیتون نیاز داریم که جکیل روی سیستم نصب بشه

اول اطمینان پیدا کنین ruby رو سیستمتون نصبه

	 ruby -v

 اگه نصب نبود دستور زیر رو برای نصب در ترمینال وارد کنین :

	 sudo apt-get install ruby ruby-dev build-essential

	 echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
	 echo 'export GEM_HOME=$HOME/gems' >> ~/.bashrc 
	 echo 'export PATH=$HOME/gems/bin:$PATH' >> ~/.bashrc 
	 source ~/.bashrc

سپس اقدام به نصب [jekyll]( https://jekyllrb.com/docs/installation/ ) میکنیم :

	gem install jekyll bundler

خب حالا تونستیم *جکیل* رو نصب کنیم 

4. برای ساخت وبلاگ جدیدمون دستورات زیر رو وارد میکنیم(شما اسم وبلاگ خوتونو بجای Your-Repository-Name وارد کنین ) :

		jekyll new Your-Repository-Name

حالا پوشه جدیدی ساخته شده که فایلهای اصلی وبلاگ داخلش قرار داره

5. در ادامه برای اینکه این فایل هارو به ریپازیتوری ساخته شده در گیت هاب انتقال بدیم کارهای زیر رو انجام بدین :

		cd Your-Repository-Name

		git init

		git remote add origin https://github.com/YourUserName/Your-Repository-Name

		git pull origin master


خب لازمه بگم دستور زیر 

	git pull origin master
	
		
برای اینه که فایل هایی مانند README.md که در ابتدای ساخت ریپازیتوریمون ساخته بودیم و داخل پوشه درون سیستممون نبود به عبارتی دانلود بشن و اونجا قرار بگیرن تا مشکلی ایجاد نشه
ازین دستور تا زمانی که تغییراتی رو بصورت مستقیم از طریق خود سایت گیت هاب  داخل ریپازیتوریتون ایجاد نکردین لزومی نداره استفاده کنین

حالا با استفاده از سه دستور زیر محتویات پوشه ساخته شده توسط jekyll رو به ریپازیتوریمون push میکنیم :

	git add .

	 git commit -m "first commit"

	git push -u origin master

خب تبریک میگم وبلاگتون ساخته شد :)

شما میتونین پست هاتون رو با پسوند md. بسازین و داخل پوشه **posts_** قرار بدین

ابتدای پستتون باید به شکل زیر باشه :

	---
	layout: post
	date: 2018-10-29 18:25:00 #For example
	title: Your-Post-Title
	---

بعنوان مثال میتونین نحوه چینش همین [پست](https://github.com/BiEffect/bieffect.github.io/blob/master/_posts/2018-10-29-build-blog-jekyll-github-pages.md) که درحال خوندنش هستین رو ببینین

اگه با مارک داون آشنایی ندارین میتونین از [اینجا]( https://virgool.io/@kiavash/markmoredown-iv2wl1gxicmu ) یاد بگیرین

در هر مرحله برای اینکه بتونین تغییرات اعمال شده رو مشاهده کنین از طریق ترمینال وارد پوشه اصلی وبلاگ بشین و دستور زیر رو وارد کنین :

	 bundle exec jekyll serve
	 
سپس با وارد کردن http://localhost:4000 در مرورگر تغییرات قابل مشاهدست

همچنین در فایل **config.yml_** میتونین title وبلاگ و سایر مشخصات مانند توضیحات رو تغییر بدین

در بخش دوم آموزش فعال کردن کامنت و نکات دیگه رو مطرح میکنم 

اگه مشکلی ایجاد شد یا ایرادی مشاهده کردین در کامنتها مطرح کنید یا ایمیل بفرستین

ممنون از وقتی که گذاشتین ;)
