---
layout: post 
series_episode: Spin-off
topic:  "ีรวมคำสั่งสำหรับรัน Jekyll"
subtitle: "เขียนก่อน โพสต์ทีหลัง"
createdDate:   2019-05-13 19:12 +0700
lastModifiedDate: 2019-05-13 19:50 +0700
categories: jekyll
tableOfContent:
 - Requirements
 - สร้าง Draft Post
tags: [web, blog, jekyll]
---

สวัสดีค่ะ วันนี้จะมาแชร์ {% include focus-text.html content="\"วิธีการเขียน Draft Post\"" %} สำหรับ{% include low-focus-text.html content="<del>สายดองโพสต์</del>" %}คนชอบเขียนทิ้งไว้เอา แล้วมาแก้ทีหลัง

EP นีเป็น EP เบาสมอง ลองทำ 2 นาทีเสร็จ มาเริ่มกันเลย!

{% include table-of-content.html header=page.tableOfContent %}

# Requirements

- มี Jekyll Blog
- เป็นสายดองโพสต์

# สร้าง Draft Post

1. เปิด Jekyll Blog ขึ้นมา
2. สร้างโฟลเดอร์ใหม่ชื่อ `_drafts` เอาไว้ที่โปรเจ็ค
3. สร้างไฟล์ `.markdown` แล้วใส่ไว้ใต้โฟลเดอร์ `_drafts`

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


   