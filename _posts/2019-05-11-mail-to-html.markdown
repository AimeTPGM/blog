---
layout: post 
topic:  ทำ form ไว้ส่ง mail จากหน้าเว็บกัน
subtitle: " "
description: "basic html และ jvavascript สำหรับส่งอีเมลล์จาก html form ไปหา email ใน portfolio หรือเว็บไซต์ของตัวเอง"
createdDate: 2019-05-11 15:52 +0700
lastModifiedDate: 2019-05-11 19:45 +0700
categories: web
tableOfContent:
 - ใช้ mailto
 - ทำ Form สำหรับส่งเมลล์
 - Link ไปที่ gmail mail compose
tags: [web, html, javascript, gmail]
---
{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/11/thumbnail.png" %}

พอดีไปเจอคำถามนึงใน facebook group ของ [สมาคมโปรแกรมเทอร์ไทย](https://web.facebook.com/groups/ThaiPGAssociateSociety/){:target="_blank"}

{% include mrA.html content="เราจะเขียนให้มันส่งเมลล์มาหาเรายังไงครับ" %}

แล้วก็แปะรูปมา 2 รูป เป็นหน้าเว็บที่มี form ไว้สำหรับส่งเมลล์ และอีกรูปหนึ่งเป็น html code

ถ้าเขียนให้ส่งเมลล์เฉยๆ หลายๆคนอาจจะเคยเห็นหรือเคยท่า mailto กันมาแล้ว แต่พอดีเค้ามีคำถามต่อว่า

{% include mrA.html content="แล้วจะให้มันเปิดไปหน้า gmail เลยยังไงครับ" %}

ก็เลยเป็นที่มาของ entry นี้ เพราะแอบไปเซิร์ด Google มา 5555

# Entry นี้มีอะไรบ้าง

{% include table-of-content.html header=page.tableOfContent %}

# ใช้ mailto

ขอเริ่มจากง่ายๆก่อนเลย คือการใช้โค้ด mailto ไว้ที่ html พอกดแล้วมันจะเปิดโปรแกรม Mail ที่อยู่ในคอมพิวเตอร์เครื่องนั้นขึ้นมา

เปิด text editor แล้วพิมพ์ลงไปแบบนี้

{% include file-name.html content="index.html" %}
```html
<a href="mailto:someone@email.com">Click to send email</a>
```

save แล้วเปิดหน้านั้นขึ้นมาบน browser

![1](/blog/assets/img/2019/05/11/1.png)

ไหนลองกด 

![2](/blog/assets/img/2019/05/11/2.png)

ฮั่นแหน่~ พอกดแล้วมีโปรแกรม Mail ขึ้นมาจริงด้วย 

แต่ไม่มีเนื้อหาหรือหัวข้ออะไรในอีเมลล์เลย

ถ้าอยากเพิ่มหัวข้อหรือเนื้อหาในเมลล์ ใส่โค้ดเพิ่มไปแบบนี้

{% include file-name.html content="index.html" %}
```html
<a href="mailto:someone@email.com?subject=หัวข้อ&body=เนื้อหา">Click to send email</a>
```

save แล้วไป refresh พอ click แล้วจะได้แบบนี้

![3](/blog/assets/img/2019/05/11/3.png)

{% include additional.html id="1" topic="ถ้า Mail ขึ้นเป็นภาษาต่างดาว" 
    text='<p>ถ้ากดแล้วตัว Mail ขึ้นเป็นภาษาต่างดาว ให้เพิ่ม<em>meta utf-8</em> เข้าไปใน <em>head</em> ด้วย แบบนี้</p>
    <pre class="highlight">&lt;head&gt;&lt;meta charset="UTF-8"&gt;&lt;/head&gt;</pre>' %}

# ทำ Form สำหรับส่งเมลล์

ถ้าอยากทำเป็น form แบบง่ายๆ มีให้กรอกชื่อ อีเมลล์ และข้อความ ก็เพิ่มโค้ดด้านล่างลงไป 

{% include file-name.html content="index.html" %}
```html
<form action="mailto:someone@email.com" method="post" enctype="text/plain">
    ชื่อ: <input type="text" name="name"/><br>
    อีเมลล์: <input type="text" name="email"/><br>
    ข้อความ:  <input type="text" name="message"/><br>
    <input type="submit" value="send"/>
    <input type="reset" value="reset">
</form>
```

ไหนลองสิ้

![4](/blog/assets/img/2019/05/11/4.png)

ใช้ได้! แต่ ... เสียใจด้วย มันไม่ support ภาษาไทย 

ถ้าอยากให้ support เรามาแก้โค้ดแล้วใส่ javascript เพิ่มเข้าไปอีกนิดนึงกัน

- ลบ `action` และ `enctype` ออก 
- ใส่ `id` ให้ครบทุกๆ `input` แล้วเพิ่ม javascript โค้ดใน `<script></script>`
- ใส่ `onclick="sendMail()"` ให้ปุ่ม submit
  
{% include file-name.html content="index.html" %}
```html
<form>
    ชื่อ: <input type="text" name="name" id="name"/><br>
    อีเมลล์: <input type="text" name="email" id="email" /><br>
    ข้อความ:  <input type="text" name="message" id="message" /><br>
    <input type="submit" value="send" onclick="sendMail()" />
    <input type="reset" value="reset">
</form>

<script>
    const sendMail = () => {
        const name = document.getElementById('name').value;
        const email = document.getElementById('email').value;
        const message = document.getElementById('message').value;
        window.open(`mailto:someone@email.com?subject=เมลล์จากคุณ${name+' '+email}&body=${message}`);
    }
</script>
```

เวลากดปุ่ม Submit ตัว Browser จะเปิดหน้าใหม่แล้วเปิดโปรแกรมเมลล์ขึ้นมาพร้อมข้อความที่เรา set เอาไว้ในตัวแปร subject กับ body ของ mailto 

ลองกรอก form แล้วส่งดู จะได้แบบนี้

![5](/blog/assets/img/2019/05/11/5.png)

ประมาณนี้ สำหรับ basic mailto ที่จะเอาไปใช้กับเว็บของตัวเองกัน

# Link ไปที่ gmail mail compose

กลับมาที่คำถามที่ 2 ของมิสเตอร์ A

{% include mrA.html content="แล้วจะให้มันเปิดไปหน้า gmail เลยยังไงครับ" %}

นี้เลยไป Google มา แล้วได้ความว่า {% include focus-text.html content="แทนที่เราจะใช้ mailto เราให้มันเปิดหน้า mail compose ของ Gmail เลยก็ได้" %} 

{% include low-focus-text.html content="วิธีการนี้ทดสอบแล้วว่าใช้ได้ล่าสุดวันที่ 11 May 2019 หลังจากนี้อาจมีการเปลี่ยนแปลง ถ้า gmail มีการอัพเดต" %}

เปิดไฟล์เดิมของเราขึ้นมา แล้วเปลี่ยนค่าใน `mailto` ให้เป็นลิ้งไป gmail

```
https://mail.google.com/mail/u/0/?view=cm&ui=2&tf=0&fs=1&to=someone@email.com&su=หัวข้อ&body=ข้อความ
```

{% include file-name.html content="index.html" %}
```html
<form>
    ชื่อ: <input type="text" name="name" id="name"/><br>
    อีเมลล์: <input type="text" name="email" id="email" /><br>
    ข้อความ:  <input type="text" name="message" id="message" /><br>
    <input type="submit" value="send" onclick="sendMail()" />
    <input type="reset" value="reset">
</form>

<script>
    const sendMail = () => {
        const name = document.getElementById('name').value;
        const email = document.getElementById('email').value;
        const message = document.getElementById('message').value;
        window.open(`https://mail.google.com/mail/u/0/?view=cm&ui=2&tf=0&fs=1&to=someone@email.com&su=เมลล์จากคุณ${name+' '+email}&body=${message}`);
    }
</script>
```

ลองส่งเมลล์กัน กรอกข้อความใน form เหมือนเดิม

![6](/blog/assets/img/2019/05/11/6.png)

พอกดปุ่ม submit แล้วมันจะเด้งเปิดหน้าใหม่ขึ้นมาเป็น gmail compose 

![7](/blog/assets/img/2019/05/11/7.png)

จบ!

หมดแล้วค่า สำหรับ basic html ในการส่งเมลล์ การทำ form ส่งเมลล์ พร้อมเพิ่ม javascript อีกเล็กน้อย เอาไว้ link ไปหน้า compose email ของ gmail สำหรับใครที่อยากใช้ gmail เป็นหลัก

{% include focus-text.html content="แต่มีข้อควรระวังนิดนึงสำหรับการ link ไป gmail"%} คือ ...
- เราไม่สามารถการันตีได้ว่า user ของเราทุกคนจะใช้ gmail บางคนอาจใช้ outlook, hotmail, yahoo หรือกระทั่งเมลล์ของบริษัทเค้า
- จากข้อเมื่อกี้ควรมี condition ดักไว้ว่าจะใช้ mailto หรือจะให้ลิ้งไป gmail โดยเขียน javascript ก็ได้ ว่าถ้าเจอ gmail.com ในอีเมลล์ของ user ให้ link ไปหน้า compose mail ของ gmail ทันที
- ถ้า user ไม่ได้ล็อกอินไว้ gmail จะ force user ไปที่หน้า login ก่อนถึงจะกลับเข้าหน้า compose เมลล์ที่เราเขียนให้ลิ้งไป
- วิธีการ link ไป gmail ยังใช้ได้อยู่(11 May 2019) แต่ถ้ามีการอัพเดตหรือเปลี่ยนแปลง link จาก google เมื่อไหร่ ก็อย่าลืมเปลี่ยนตามด้วยนะจ้ะ

Entry นี้ขอหยุดไว้เท่านี้ก่อน ไว้เจอกันใหม่จ้า

{% include signature.html %}