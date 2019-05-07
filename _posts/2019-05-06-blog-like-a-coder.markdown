---
layout: post 
series_episode: I
topic:  "มาทำ Blog ด้วย Jekyll กันดีกว่า"
subtitle: "เบื่อแล้ว บล็อกคนอื่น ทำเอง นักเลงพอ"
createdDate:   2019-05-06 16:15 +0700
lastModifiedDate: 2019-05-07 11:30 +0700
categories: jekyll
tableOfContent:
 - [ทำไมต้อง Jekyll, ทำไมต้อง-jekyll ]
 - [ก่อนทำ Blog, ก่อนทำ-blog]
 - [Requirements, requirements]
 - [ลง Jekyll กันเลย, ลง-jekyll-กันเลย]
 - [โครงสร้างของ project, โครงสร้างของ-project]
 - [แก้หน้าแรกของเพจดูกันดีกว่า, แก้หน้าแรกของเพจดูกันดีกว่า]
 - [เขียน First Entry ของตัวเอง, เขียน-first-entry-ของตัวเอง]
tags: [web, blog, jekyll]
---

{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/thumbnail1.png" %}

# เฮลโล๊

ขอประเดิม entry แรก ด้วยการทำ blog ที่ทำให้เกิด blog นี้ขึ้นมา เอาฤกษ์เอาชัยกันหน่อยจ้า

{% include blog-quote.html content="(เว้นที่ไว้ตัดริบบิ้น)" %}

# เริ่ม

แรกเริ่มเดิมทีคืออยากจะหาที่เขียนบล็อกสักที่หนึ่ง เคยลองเขียนไว้ใน [wordpress.com](https://www.wordpress.com){:target="_blank"} แบบที่เป็นเว็บ template แล้ว แต่ก็ทิ้งไป เพราะไม่ค่อยได้เข้าไปใช้บ่อยๆ แถม customize อะไรไม่ค่อยได้ 

เลยเปลี่ยนมาใช้ [wordpress.org](https://www.wordpress.org){:target="_blank"} แทน แต่ยังไม่ตอบโจทย์ รู้สึก setup ยุ่งยาก แถมต้องไปหาที่โฮสติ้งอีก อะไรอีก {% include hashtag.html content="#สายฟรี" %} ไม่ค่อยได้บล็อกบ่อยๆเลยจบกันไปแบบนั้นดื้อๆ

มีบ้างที่เขียนบล็อกทั่วไปแบบไม่เกี่ยวกับโปรแกรมมิ่งเอาไว้ใน {% include focus-text.html content="Facebook Page" %} (ซึ่ง unpublished ไปแล้ว เพราะไม่มีเวลามาโฟกัสกับเพจมากและหมดมุขเขียน 555+)

เคยลอง [Medium](https://medium.com/) นิดหน่อย แต่ก็ยังไม่สาแก่ไจพี่ อยากได้เป็นของตัวเองอะๆๆๆๆๆๆ

วันนึงนั่งไถๆ Facebook แล้วไปเจอโพสของน้องคนนึง เลยทำให้ได้มารู้จักกับ {% include focus-text.html content="**Jekyll**" %} ครั้งแรก

# Entry นี้มีอะไรบ้าง

{% include table-of-content.html header=page.tableOfContent %}

# ทำไมต้อง Jekyll

ก่อนจะเริ่มเขียนบล็อกด้วย Jekyll ขอพื้นที่ในการขิงและความประทับใจที่ได้ลองจับเจอกิ้วมาปู้ยี้ปู้ยำด้วยตัวเอง 

- เขียนง่าย เริ่มง่าย อาจจะเข้าใจยากช่วงแรก แต่เดี๋ยวก็ง่าย (อะไรวะ)
- ตัว content ใน บล็อกเองเขียนด้วยภาษา markdown เข้าใจง่าย (readme ใน github ก็ใช้ markdown)
- ไม่ต้องมีหลังบ้าน เพราะมันอ่าน markdown ในตัวมันเอง
- Customize ได้ตามใจฉัน เขียนเอง บล็อกเอง นักเลงพอ
- มี official theme ให้ใช้ สำหรับคนขี้เกียจเขียนเองทั้งหมด
- รู้สึกเหมือนเขียนไป โค้ดไป ฟินดี
- เป็น static site เอาไป deploy ที่อื่นก็ได้ อย่าง netify ไรงี้ (เพิ่ง Google มา)
- ถ้าใช้ร่วมกับ Github Page ก็คือ ฟรี!
- ด้วยความเป็น static site มันโหลดไวเว่อร์มาก
- สามารถ Migrate Blog Content จากที่อื่นมาไว้ที่นี่ได้ หรือจากที่นี่ไปที่อื่นก็ได้อีก (ถามอากู๋เอา มีเยอะแยะ)
- (น่าจะมีอีก แต่นึกไม่ออก)

ข้อเสีย ก็พอมีอยู่เหมือนกัน เช่น

- ตอนแรกงงๆ ไม่รู้จะปรับแก้หน้าตาของมันยังไง ต้องใช้เวลาอ่านนิดนึง
- ใครไม่เคยจับ ruby เห็นตอนแรกอาจจะกลัว แต่จริงๆมันไม่ได้ require ruby skill ขนาดนั้น
- ถ้ามีบล็อกเยอะมากๆๆๆๆๆๆๆๆๆๆๆๆ อาจจะใช้เวลาในการ bundle นาน (ไม่แน่ใจนะ ยังไปไม่ถึงจุดนั้น)
- เขียนไป โค้ดไป โค้ดเพลินไป เขียนบล็อกไม่เสร็จสักที (ฮา)
- ต้องพอเขียนโค้ดเป็นบ้าง แต่ถ้าไม่เป็นเลย ก็เริ่มเรียนจากตรงนี้ก็ได้

ตามนั้นค่ะ weight ข้อดีข้อเสียกับตัวเอง แล้วตัดสินใจดู ก็เออ เอาวะ! ตี 2 ของคืนหนึ่งก็โหลด jekyll มานั่งเล่นดู

{% include low-focus-text.html content="ส่วนตัว แทบไม่ได้แตะรูบี้มาก่อน แต่โครงสร้างของ Jekyll มันคล้าย Python Django ถ้าใครเคยเขียนมาก่อน ก็น่าจะสบายหน่อยค่ะ" %}

# ก่อนทำ Blog

เกริ่นคร่าวๆก่อนว่า Jekyll มันทำงานยังไง {% include low-focus-text.html content="เอาตรงๆ ก็เพิ่งจับมาแค่วันนิดๆ ผิดถูกขออภัยนะฮะ" %}

{% include blog-quote.html content="Jekyll จะ complie ไฟล์ .markdown ในโฟลเดอร์ <em>_posts</em> แล้วเอาไป generate เป็น .html" %}

จบ 

คือไฟล์ .markdown มันจะอยู่ในรูปแบบ ```yyyy-MM-dd-blog-name.markdown``` หลังจาก complie ไฟล์นี้จะถูก generate เป็น ```~/yyyy/MM/dd/blog-name.html``` นะเอง

แต่! ยังไม่หมด jekyll มีฟังก์ชั่นสำหรับทำ category มาให้ด้วย อู้หูววว

เวลาเราเขียนบล็อกที่หัวของไฟล์จะมีหน้าตาประมาณนี้

{% include file-name.html content="2019-05-06-blog-like-a-coder.markdown" %} 
```ruby
---
layout: post                            # เลย์เอ้าที่เอามาใช้โชว์หน้าตาบล็อก เดี๋ยวจะพูดถึงทีหลัง
topic:  "มาทำ Blog ด้วย Jekyll กันดีก่า"    # ชื่อบล็อก
date:   2019-05-06 16:15 +0700          # วันที่เขียนบล็อก
categories: jekyll                      # category อยู่กงนี้
---

เขียน content ของ blog ตรงนี้
```

พอ compile ปึ๊บ ไฟล์นี้จะถูก generate ไว้ที่ ```~/jekyll/2019/05/06/blog-like-a-coder.html``` นั่นเองจ้า

# Requirements

- คอมต้องมี [Ruby](https://www.ruby-lang.org/en/) ถ้าไม่มี install ก่อนนะจ้ะ
- ใช้ command line ได้บ้าง
- {% include low-focus-text.html content="ถ้าอยากเอาขึ้น github page" %} ใช้ Git command line ได้เบื้องต้น หรือใช้ UI Tools ก็ไม่ว่ากัน

# ลง Jekyll กันเลย

1. ลง [Ruby](https://www.ruby-lang.org/en/){:target="_blank"} ในคอมกันก่อน ใครใช้ Windows OS อาจจะต้องหาท่าในการลงนิดนึง ส่วน MacOS, Linux มีอยู่ในเครื่องแล้วนะจ้ะ
2. ลงแล้วลองพิมพ์ ```ruby -v``` เพื่อเช็คเวอร์ชั่นและความชัวร์ว่าอยู่ใน Environment PATH แล้ว
```
$ ruby -v
ruby 2.3.7p456 (2018-03-28 revision 63024) [universal.x86_64-darwin18]
```
3. ลง jekyll bundler ```gem install jekyll bundler```
4. สร้าง Jekyll site ของตัวเอง
```
$ cd ~/path/to/your/workspace
$ jekyll new blog
Running bundle install in /path/to/your/workspace/blog... 
.
.
.
New jekyll site installed in /path/to/your/workspace/blog
```
เท่านี้เราก็จะได้ Jekyll site พร้อม theme เริ่มต้นไว้ใช้งานแล้วจ้า 
5. อยากจะลองรันขึ้นมาดูก็ ```bundle exec jekyll serve --watch``` บล็อกของเราจะไปรันที่ ```localhost:4000```

![1](/blog/assets/img/2019/05/1.png)

# โครงสร้างของ project

ถ้าเข้าไปดูใน root โฟลเดอร์ที่เราเพิ่งสร้างมาเมื่อกี้ จะเจอไฟล์ต่างๆประมาณนี้
```
blog
│   _config.yml         // เอาไว้เซ็ต config ของโปรเจ็ค
│   .gitignore
│   404.html            // ถ้าหา page ไม่เจอ จะเข้าหน้านี้
│   about.md            // content หน้า about
│   Gemfile             // สำหรับ install dependencies ต่างๆ
│   Gemfile.lock
│   index.md            // content ของหน้าแรก
│
└─── _posts
│   │
│   └─ 2019-05-06-welcome-to-jekyll.markdown    // ไฟล์ Blog แรกของเรา เย้!
│
└─── _sites             // เวลารัน local ไฟล์ต่างๆจะคอมไพล์มาไว้ที่โฟลเดอร์นี้
│
└─── _sass-cache

```

# แก้หน้าแรกของเพจดูกันดีกว่า 

หน้าแรกของเพจจะเริ่มต้นอ่านที่ ```index.md``` เสมอ

{% include file-name.html content="index.md" %} 
```ruby
---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
```

{% include focus-text.html content="**TL;DR**" %} 

ใน ```_config.yml``` แก้บรรทัดต่อไปนี้ ตามใจชอบเลย

```
title: title ของเพจ
email: ใส่อีเมลล์ตรงนี้
description: >- 
    ข้อความอธิบายเพจสั้นๆ สัก 3-4 บรรทัด
baseurl: "/blog/" 
url: "https://github-username.github.io"   # เปลี่ยน github-username เป็น username ของตัวเอง
twitter_username: ยูสเซอทวิตเตอร์
github_username:  ยูสเซอกิตฮับ
```

กด save สั่ง ```bundle exec jekyll serve --watch```

แล้วไปดูที่ ```localhost:4000/blog/``` หน้าตาก็จะเปลี่ยนไปตามที่เราแก้จ้า

![2](/blog/assets/img/2019/05/2.png)

{% include focus-text.html content="**ทำไมล่ะ?**" %}

{% include focus-text.html content="**คำเดือน: ยาวมาก ข้ามไปเขียนบล็อกก่อนได้ ทำไปเรื่อยๆเดี๋ยวก็เข้าใจเอง**" %}

ถ้าเราเข้าไปดูที่ไฟล์ ```index.md``` จะเจอโค้ดนี้

```
---
layout: home
---
```

หมายความว่าหน้าแรก ใช้ layout จาก ```home.html``` ว่าแต่ ... ```home.html``` นี่มันอยู่ที่ไหนล่ะ???

นี่เลยจ่ะ ไปดู ```_config.yml``` Line 29 จะเห็นว่า theme ที่ใช้เริ่มต้นคือ ```theme: minima```

{% include blog-quote.html content="คืองี้ ถ้าเอาแบบอย่างง่าย jekyll ของเรา จะ extends theme มาจาก theme ที่เรา defines ไว้ใน <em>_config.yml</em> พอ compile มันจะดึง theme นั้นมา generate html code แล้ว inject content ของ blog เราเข้าไป" %}

ดังนั้นเราต้องไปดู theme minima ว่าเค้าเขียน ```home.html``` ไว้ยังไง

{% include focus-text.html content="ดูที่ไหน?" %} เข้า [Github ของ Jekyll](https://github.com/jekyll/){:target="_blank"} โลด ข้างในจะมี plugin และ theme repo เต็มไปหมด {% include low-focus-text.html content="[theme minima จิ้มตรงนี้](https://github.com/jekyll/minima)" %}

เข้าไปดูที่ ```_layouts/home.html``` จะเจอประมาณนี้

{% include file-name.html content="_layouts/home.html" %} 
```ruby
---
layout: default
---

<!-- code html ต่างๆ -->
```

แปลว่า ```home.html``` extends มาจาก ```default.html``` อีกที

อ่ะ ไหนลองไปดู ```default.html``` ดูสิ้ โหย เจอโค้ดนี้หว่ะ

{% include file-name.html content="_layouts/home.html" %} 
```ruby
{% raw %}
{%- include header.html -%}
{% endraw %}
```
แปลว่า ```default.html```  มันเอา templates includes มาจาก ```_includes/header.html```

เราก็ trace ไปต่อ เปิดไฟล์นั้นขึ้นมาค่ะ!! {% include hashtag.html content="#ไปค่ะพี่สมหมาย" %}

{% include file-name.html content="_includes/header.html" %} 
```ruby
<a class="site-title" rel="author" href="{{ "/" | relative_url }}">{% raw %}{{ site.title | escape }}{% endraw %}</a>
```

เจอแล้ว!!! ไอเจ้า ```site.title``` ก็คือเอาค่ามาจาก ```title: title ของเพจ``` ที่อยู่ใน ```_config.yml``` นั่นเอง

ดังนั้นเรามองอย่างง่ายว่า ```site``` ก็คือ object ที่เอามาจาก ```_config.yml``` ก็พอไหวอยู่

นี่แหล่ะ ที่มาของการแก้ ```_config.yml``` แล้วการแสดงผลในหน้าแรกมันเปลี่ยนไป

ถ้าเราเพิ่ม ```myvar: foobar``` ใดๆ ใน ```_config.yml``` แล้วอยากดึงมาใช้ด้วย ```site.myvar``` ได้เหมือนกัน

# เขียน First Entry ของตัวเอง

ตามที่เกริ่นไว้แล้วใน [ก่อนเริ่ม Blog แรก](#ก่อนเริ่ม-blog-แรก) การเขียนบล็อกใน jekyll นั้นง่ายมาก

แค่เราสร้างไฟล์ที่มี format ```yyyy-MM-dd-blog-name.markdown``` เอาไว้ในโฟลเดอร์ ```_posts```

Jekyll ก็จะ generate ไฟล์ html ที่เป็นหน้าใหม่ พร้อมลิ้งให้เราอัตโนมัติ!

1. รัน jekyll server ก่อน ```bundle exec jekyll serve --watch```

2. สร้างไฟล์ใหม่ สมมติว่าชื่อ ```2019-05-06-first-blog.markdown``` เอาไว้ที่ ```_posts``` 
{% include low-focus-text.html content="ชื่อไฟล์ใช้ภาษาอังกฤษนะจ้ะ ลองภาษาไทยแล้วไม่เวิร์ค" %}

{% include file-name.html content="_posts/2019-05-06-first-blog.markdown" %} 
```ruby
---
layout: post
title:  "บล็อกแรกเลยเธอ"
date:   2019-05-06 18:33:25 +0700
categories: diary
---

บล็อกซะหน่อยจ้า

# หัวข้อ 1
## หัวข้อ 2

**ตัวหนา**

_ตัวเอียง_
```

กด save แล้วไปดูที่ ```localhost:4000/blog/``` จะเจอ entry ใหม่เข้ามา

![3](/blog/assets/img/2019/05/3.png)

![4](/blog/assets/img/2019/05/4.png)

จบละเธอ อีซี่ 

ถ้าอยากเอาขึ้น github ก็สร้าง repo ใหม่ขึ้นมา แล้ว push code ขึ้นไปที่ master branch เลย

ที่ repo นั้น ไปที่ ```setting > Github page``` เลือก master branch รอแป้บนึง เพจเราจะดีพลอยไปที่ https://your-github-username.github.io/blog/ (เดี๋ยวมาเขียนแบบละเอียดอีกที)

หลังจากนี้จะ Add Entry ใหม่ ก็เพิ่มไฟล์ใหม่ใช้ format ```yyyy-MM-dd-blog-name.markdown``` ไปเรื่อยๆ แค่นี้ก็ได้บล็อกมาใช้ละ

ตัวบล็อกเขียนด้วยภาษา markdown และ kramdown 

{% include low-focus-text.html content="[markdown syntax จิ้มตรงนี้จ่ะ](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)" %}

{% include low-focus-text.html content="[kramdown doc จิ้มตรงนี้](https://kramdown.gettalong.org/documentation.html)" %}

{% include focus-text.html content="**แต่เว็บดูจืดๆไม่สวยเลย :(**" %} 

ใช่จ้า เอ็นทรี่หน้าเดี๋ยวมาเขียน Tutorial สำหรับเขียนแต่งหน้า blog ตัวเอง เพราะรู้สึกว่ามันชักจะยาวเกินไปละ

เอาไว้ว่างๆ จะมาอัพเดต

วันนี้ไปแร้วนะ มุฟมิฟ

{% include signature.html %}