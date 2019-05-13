---
layout: post 
series: ทำ Blog ด้วย Jekyll
series_episode: Spin-off
topic:  "วิธีสร้าง Draft Post ใน Jekyll"
subtitle: "เขียนก่อน โพสต์ทีหลัง"
createdDate:   2019-05-13 19:12 +0700
lastModifiedDate: 2019-05-13 20:17 +0700
categories: jekyll
tableOfContent:
 - Requirements
 - สร้าง Draft Post
tags: [web, blog, jekyll]
---

{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/13/draft/thumbnail.png" %}

สวัสดีค่ะ วันนี้จะมาแชร์ {% include focus-text.html content="\"วิธีการเขียน Draft Post\"" %} สำหรับ{% include low-focus-text.html content="<del>สายดองโพสต์</del>" %}คนชอบเขียนทิ้งไว้เอา แล้วมาแก้ทีหลัง

EP นีเป็น EP เบาสมอง ลองทำ 2 นาทีเสร็จ มาเริ่มกันเลย!

{% include table-of-content.html header=page.tableOfContent %}

# Requirements

- มี Jekyll Blog
- เป็นสายดองโพสต์

# สร้าง Draft Post

1. เปิด Jekyll Blog ขึ้นมา
2. สร้างโฟลเดอร์ใหม่ชื่อ `_drafts` เอาไว้ที่โปรเจ็ค
3. สร้างไฟล์ `.markdown` แล้วใส่ไว้ใต้โฟลเดอร์ `_drafts` {% include focus-text.html content="โดยไฟล์ Draft ไม่ต้องใส่วันที่ ใช้แค่ชื่อก็พอ" %} เช่น my-first-draft.markdown

โปรเจ็คจะหน้าตาประมาณนี้

```
~/blog/
|   _config.yml        
|   .          
|   . ไฟล์ต่างๆ  
|   .                       
|
└─── _posts/
|
└─── _drafts/       <<<<< สร้างโฟลเดอร์นี้
    |   my-first-draft.markdown    <<<<< Draft ใดๆ เอามาใส่ไว้ใต้โฟลเดอร์
```

สำหรับไฟล์ `my-first-draft.markdown` เขียนเหมือน Blog ปกติไปเลย

เปิด cmd/Terminal ขึ้นมา แล้วสั่ง `bundle exec jekyll serve --drafts`

เปิด Browser ไปที่ `localhost:4000/blog/` จะเจอไฟล์ draft ของเรา list เอาไว้ด้วย

![1](/blog/assets/img/2019/05/13/draft/1.png)

![2](/blog/assets/img/2019/05/13/draft/2.png)

เท่านี้เราก็สามารถ `git push` ขึ้นไปได้ โดยที่ jekyll จะไม่ build เอา draft ของเราไปโชว์ในบล็อกด้วย (จะโชว์แต่ post ที่อยู่ในโฟลเดอร์ `_posts` เท่านั้น)

ถ้าเราอยากจะ publish ขึ้นบล็อก ก็แค่ย้ายจากโฟลเดอร์ `_drafts` ไปโฟลเดอร์ `_posts` ก็เป็นอันเสร็จ (อย่าลืมใส่วันที่ด้วย)

ขอบคุณ Jekyll ที่ทำให้การเขียน draft สุดสะดวก

จบการรายงาน,

เอมมี่

{% include signature.html %}



   