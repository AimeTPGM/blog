---
layout: post 
series: Jekyll Blog
series_episode: II
topic:  "เอา Jekyll Blog ขึ้น Github Page กัน"
subtitle: "พอจะมีเวลาว่างสัก 5 นาทีไหม?"
createdDate:   2019-05-08 18:22 +0700
lastModifiedDate: 2019-05-09 23:31 +0700
categories: jekyll
tableOfContent:
 - Requirements
 - สร้าง Github Repo
 - Push Blog ขึ้น Git
 - Configure Github Page
tags: [web, blog, jekyll, git, github, github page]
---

{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/08/thumbnail.png" %}

ต่อจาก [Part I มาทำ Blog ด้วย Jekyll กันดีกว่า](/blog/jekyll/2019/05/06/blog-like-a-coder.html) วันนี้เราจะอัพบล็อกของเราไปโฮสไว้ที่ {% include focus-text.html content="Github Page" %} ซึ่งให้ Developer โฮสต์ Repository ของตัวเองได้ฟรีๆกัน 

# Entry นี้มีอะไรบ้าง

{% include table-of-content.html header=page.tableOfContent %}

# Requirements

- ลง [Git](https://git-scm.com/downloads) Command เอาไว้ในเครื่องแล้ว (หรือจะใช้ UI Tools อย่าง [Sourcetree](https://www.sourcetreeapp.com/) ก็ได้ แต่ Blog นี้จะใช้ command line เป็นหลักนะคะ)

# สร้าง Github Repo

1. Login เข้า [Github](https://github.com/) ของตัวเอง
2. กด + ที่มุมขวาบน เลือก New Repository
   ![1](/blog/assets/img/2019/05/08/1.png)
3. ใส่ชื่อ repository เป็น blog (หรืออย่างอื่นก็ได้ แต่ต้องเหมือน baseurl ใน `_config.yml`)
   ![2](/blog/assets/img/2019/05/08/2.png)
4. สร้างเสร็จจะขึ้นหน้าแบบนี้
   ![3](/blog/assets/img/2019/05/08/3.png)

# Push Blog ขึ้น Git

1. เปิดไฟล์ `~/blog/Gemfile` ขึ้นมา แล้วใส่บรรทัดนี้ลงไปล่างสุด
```
gem 'github-pages', group: :jekyll_plugins
```
2. เปิด cmd หรือ Terminal ขึ้นมา change directory ไปที่ Jekyll Blog ของตัวเอง
```
$cd ~/path/to/your/blog
```
3. สั่งให้ download dependency
```
$bundle install
```
4. config git ใน folder นั้น
```
$ git init
$ git remote add origin https://github.com/AimeTPGM/blog.git
```
3. add ทุกอย่างขึ้นไป แล้ว push ขึ้น Github เลย {% include low-focus-text.html content="ตอนสร้างโปรเจ็ค Jekyll ขึ้นมา Jekyll ทำไฟล์ .gitignore ให้เราอยู่แล้ว เราไม่ต้องกลัวว่าจะ push ไฟล์ขยะขึ้นไปบน git ค่ะ" %}
```
$ git add .                          # add ทุกอย่างเข้า git
$ git commit -am "init my blog"      # comment เกี่ยวกับ change นี้สักหน่อย
$ git push origin master             # push ขึ้น github กันเลย
```
1. กลับไปที่ browser แล้ว refresh หนึ่งที จะเห็นเว็บแบบนี้ แปลว่า code และ blog ของเราขึ้นไปอยู่บน Github แล้ว ครั้งต่อไปที่เราเขียนบล็อกเพิ่ม ก็ repeat step 3 เราจะเห็น entry ใหม่เพิ่มขึ้นทันที
   ![4](/blog/assets/img/2019/05/08/4.png)


{% include focus-text.html content="**แต่ยังไม่จบ!**" %} เราต้อง setup ที่ Github ของเราอีกนิดหน่อย เว็บบล็อกของเราถึงจะขึ้นโชว์ที่ https://your-github-username.github.io/blog/

# Configure Github Page

1. ไปที่แถบ Setting
   ![5](/blog/assets/img/2019/05/08/5.png)
2. เลื่อนลงไปจนเจอ Github Page Setting
   ![6](/blog/assets/img/2019/05/08/6.png)
3. เปลี่ยนให้ดึงมาจาก master branch
   ![7](/blog/assets/img/2019/05/08/7.png)
   ![8](/blog/assets/img/2019/05/08/8.png)
4. รอแป๊บนึง แล้วเข้าไปดูที่ https://your-github-username.github.io/blog/ จะเห็นว่า Blog ของเราได้ Publish ขึ้น Github Page เป็นที่เรียบร้อย~ เยยยย้
   ![9](/blog/assets/img/2019/05/08/9.png)

เห็นไหมว่าเอา Jekyll Blog ขึ้น Github Page ง่ายนิดเดียว ใช้เวลาแค่ 5 นาทีก็ได้เว็บ Blog เป็นของตัวเองแล้ว นี่ก็เลยเป็นอีกหนึ่งเหตุผลที่เลือก Jekyll มาใช้ 

{% include low-focus-text.html content="[อ่านเพิ่มเติมเกี่ยวกับ Jekyll Gihub Page จิ้ม](https://jekyllrb.com/docs/github-pages/){:target='_blank'}" %}

{% include low-focus-text.html content="[วิธี deploy แบบอื่นๆ จิ้ม](https://jekyllrb.com/docs/deployment/){:target='_blank'}" %}

ใครที่กำลังมองหา Tools ทำเว็บ Blog ขำๆของตัวเอง เราว่า Jekyll เป็นตัวเลือกที่ดี 

ยิ่งสำหรับคนที่ชอบ Customize อยาก Blog ไป โค้ดไป Jekyll เป็นของเล่นชิ้นดีสำหรับคุณเลยหล่ะ :D

ไว้ Entry หน้าจะมาพูดถึงเรื่องการแต่ง Theme จาก Official Theme ของ Jekyll

วันนี้ขอตัว ไปละ โชคดีค่ะ ฟิ้วววว~

{% include signature.html %}

