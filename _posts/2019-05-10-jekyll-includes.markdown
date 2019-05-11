---
layout: post 
series: ทำ Blog ด้วย Jekyll
series_episode: IV
topic:  "เขียน component templates กับ include ใน Jekyll"
subtitle: "DRY – Don't Repeat Yourself"
description: "เลิกเขียนโค้ดซ้ำๆ พร้อมเพิ่มลูกเล่นให้ blog post ให้น่าอ่านบน jekyll"
createdDate: 2019-05-10 19:30 +0700
lastModifiedDate: 2019-05-11 17:39 +0700
categories: jekyll
tableOfContent:
 - Requirements
 - เพิ่มลูกเล่นให้ Blog post
 - สร้าง component
 - ใช้ component
 - แล้วเราจะเขียน component อะไรมาใช้ได้บ้างล่ะ?
tags: [web, blog, jekyll]
---
{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/10/thumbnail.png" %}

อันนี้เป็น EP สุดท้ายสำหรับเนื้อหาหลักในซีรี่ส์ [ทำ Blog ด้วย Jekyll](/blog/series/#ทำ-blog-ด้วย-jekyll) แล้ว ที่เหลือจะเป็น Spin-off สำหรับการเอาความรู้พื้นฐานของการทำ Jekyll Blog มาดัดแปลง

ใครที่ตามอ่านมาจาก [EP1](/blog/jekyll/2019/05/06/blog-like-a-coder.html){:target="_blank"}, [EP2](/blog/jekyll/2019/05/08/jekyll-github-page.html) หรือ [EP3](/blog/jekyll/2019/05/08/jekyll-github-page.html) เปิดโค้ด Jekyll Blog ของตัวเองขึ้นมาใน Text Editor แล้วมาเริ่มโค้ดกันได้เลย!

# Entry นี้มีอะไรบ้าง

{% include table-of-content.html header=page.tableOfContent %}

# Requirements

- มี Jekyll Blog ของตัวเองแล้ว (ถ้ายังไม่มี อย่าลืมอ่านบทความก่อนหน้าในซีรี่ย์นี้ จะได้ทำบล็อกไปพร้อมๆกัน)
- สั่ง `bundle exec jekyll serve` รอไว้เลย แล้วเริ่มทำกัน!

# เพิ่มลูกเล่นให้ Blog post

ปกติเวลาเราเขียน entry ใหม่ขึ้นมาใน blog เราแค่สร้างไฟล์ไว้ที่โฟลเดอร์ `_posts` ด้วยฟอร์แมต `yyyy-MM-dd-blog-name.markdown` แล้วบอกว่าจะใช้ `post` เป็น layout template ไว้ที่หัวไฟล์(front matter)แบบนี้

{% include file-name.html content="_posts/2019-05-10-example-blog.markdown" %} 
```html
---
layout: post
title: "ลองเขียนเล่นๆ"
date: 2019-05-10 00:00 +0700
---
# Markdown 
<!-- ลองเขียน markdown -->
# หัวข้อ 1
## หัวข้อ 2
### หัวข้อ 3
[ลิ้ง](link)


# Html
<!-- ลองเขียน html -->
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<div>แบ่ง division ได้ด้วย</div>

{% raw %}
# Liquid tag
<!-- เขียน liquid tag -->
{% if page.title %}
    ชื่อหัวข้อ: {{ page.title }}
{% else %}
    ไม่มีชื่อหัวข้อ
{% endif %}
{% endraw %}
```

save > refresh เปิด `localhost:4000` แล้วกดที่บล็อก "ลองเขียนเล่นๆ" จะเห็นแบบนี้

![1](/blog/assets/img/2019/05/10/1.png)

{% include focus-text.html content="สมมติว่า..." %}

เราเขียนบล็อกไปเรื่อยๆ แล้วอยากจะ<span style="color: #159957;">เน้นข้อความ</span>ให้มันดูเด่นขึ้นมา เราสามารถใช้ html กับ css เขียนในเนื้อหาของบล็อก เพื่อช่วยเปลี่ยนสีเฉพาะข้อความที่เราอยากเน้นได้ ตัวอย่างเช่น

{% include file-name.html content="_posts/2019-05-10-example-blog.markdown" %} 
```html
---
layout: post
title: "ลองเขียนเล่นๆ"
date: 2019-05-10 00:00 +0700
---

ลองเขียนบล็อกดู 

ฮั่นแน่ ชอบ<span style="color: #159957;">ไฮไลท์</span>เหรอ
```

กด save แล้วไป refresh ได้ผลลัพธ์ออกมาเป็นแบบนี้

![2](/blog/assets/img/2019/05/10/2.png)

{% include focus-text.html content="ลองดูโค้ดข้างล่างนี้" %}

{% include file-name.html content="_posts/2019-05-10-example-blog.markdown" %} 
```html
---
layout: post
title: "ลองเขียนเล่นๆ"
date: 2019-05-10 00:00 +0700
---

ลองเขียนบล็อกดู 

ฮั่นแน่ ชอบ<span style="color: #159957;">ไฮไลท์</span>เหรอ

ฮั่นแน่ ชอบ<span style="color: #159957;">ไฮไลท์</span>เหรอ

ฮั่นแน่ ชอบ<span style="color: #159957;">ไฮไลท์</span>เหรอ

ฮั่นแน่ ชอบ<span style="color: #159957;">ไฮไลท์</span>เหรอ
```

แล้วถามว่าถ้าเราอยากจะเปลี่ยนสีไฮไลท์ทุกที่ ให้เป็นสีอื่น ด้วย<u>สีเดียวกัน</u> จะทำยังไงล่ะ?

{% include mrA.html content="ง่ายๆ กด Find แล้วก็ Replace สิครับ" %}

เออ .. ก็ได้อยู่นะ แล้วถ้าโค้ดไฮไลท์นี้ มันมีอยู่ที่ post อื่นด้วยล่ะ?

{% include mrA.html content="Find in files แล้วก็ Replace ก็ได้นะ" %}

อื้ม ... แล้วถ้าเกิด เราลืม Replace ที่ใดที่หนึ่งล่ะ?

{% include mrA.html content="ก็เปิดไปหน้านั้น แล้วค่อยไปเปลี่ยนโค้ดก็ได้" %}

แล้วถ้า style ของ span นี้ มันไม่ได้มีแค่ color ที่เราอยากจะเปลี่ยน {% include focus-text.html content="แต่ว่าอยากเพิ่ม margin, padding, border, box-shawdow, background, text-transform, font-weight, font-size ด้วยละ" %} เราต้องไปทำทุกไฟล์เลยเหรอ?

ถึงจุดนี้ วิธีการ Find & Replace ของมิสเตอร์ A จะใช้เวลาในการหาแล้วเพิ่มโค้ดมากกว่าแค่จะเปลี่ยนสี และไม่มีอะไรมาการันตีว่ามิสเตอร์ A จะไม่ลืมเพิ่มโค้ดในทุกๆจุดให้เหมือนกัน

ดังนั้นกลับมาที่ concept โปรแกรมมิ่งที่คนเขียนโค้ดอย่างพวกเราควรท่องเอาไว้ในใจเสมอ

{% include blog-quote.html content="DRY – Don't Repeat Yourself" %}

{% include blog-quote.html content="อย่าเขียนโค้ดหรือก๊อปปี้โค้ดที่มันทำงานเหมือนๆกัน แล้วเอาไปแปะไว้ตรงนั้นตรงนี้ เพราะถ้าเราอยากจะแก้ไขมันหนึ่งที่ เราต้องไปไล่แก้ที่ที่มีโค้ดนี้ให้เหมือนกันหมด" %}

ซึ่งโชคดี ที่ Jekyll มี `_includes` เอาไว้ลดการเขียนโค้ดซ้ำๆ ตอนนั่งทำบล็อก ด้วยการสร้าง component

# สร้าง component ใน Jeyll

บางที่ก็เรียกว่าเขียน template บางที่ก็เรียกว่า component แต่ตอนนี้ Web Component กำลังมาแรง เลยขอเรียกแบบนี้ละกัน เท่ดี 555+

{% include focus-text.html content="ทำไมต้องสร้าง component?" %} กลับไปอ่าน quote ด้านบน 

เราสร้าง component เพื่อลดการเขียนโค้ดซ้ำๆ ประหยัดเวลาในการกลับมาแก้โค้ดของเราในอนาคต และยังเอามันไป reuse ได้อีกด้วย!

เรียกว่าทำหนึ่งได้ถึงสาม งั้นเรามาเริ่มกันเลย

1. สร้างโฟลเดอร์ `_includes` ในโปรเจ็ค ประมาณนี้ แล้วสร้างไฟล์ชื่อ `highlight-text.html` ไว้ข้างใน
   ```
    ~/blog/
    |   _config.yml        
    |   .          
    |   . ไฟล์ต่างๆ  
    |   .                       
    |
    └─── _posts/
    |
    └─── _includes_/                    <<<<< สร้างโฟลเดอร์นี้   
        |   highlight-text.html         <<<<< สร้างอันนี้เพิ่ม
    ```
2. เอาโค้ด span เมื่อกี้ ยัดเข้าไปในไฟล์เลย
   ```html
   <span style="color: #159957;">{%raw%}{{ include.content }}{%endraw%}</span>
   ```
3. กด save เป็นอันเสร็จ

# ใช้ component

เราสร้าง component กันไปแล้ว ว่าแต่จะเอาไปใช้ยังไง?

เปิดบล็อกของเราขึ้นมาค่ะ ตะกี้
{% include file-name.html content="_posts/2019-05-10-example-blog.markdown" %} 
```html
---
layout: post
title: "ลองเขียนเล่นๆ"
date: 2019-05-10 00:00 +0700
---

ลองเขียนบล็อกดู 

ฮั่นแน่ ชอบ<span style="color: #159957;">ไฮไลท์</span>เหรอ
```

ลบ `<span>` ทั้งหลายออก แล้วใช้ liquid tag `include` แบบนี้แทน

{% include file-name.html content="_posts/2019-05-10-example-blog.markdown" %} 
```html
---
layout: post
title: "ลองเขียนเล่นๆ"
date: 2019-05-10 00:00 +0700
---

ลองเขียนบล็อกดู 
{%raw%}
ฮั่นแน่ ชอบ{% include highlight-text.html content="ไฮไลท์" %}เหรอ
{%endraw%}
```

ถ้ามีหลายอันก็
{% include file-name.html content="_posts/2019-05-10-example-blog.markdown" %} 
```html
---
layout: post
title: "ลองเขียนเล่นๆ"
date: 2019-05-10 00:00 +0700
---
{%raw%}
ลองเขียนบล็อกดู 

ฮั่นแน่ ชอบ{% include highlight-text.html content="ไฮไลท์" %}เหรอ

ฮั่นแน่ ชอบ{% include highlight-text.html content="ไฮไลท์" %}เหรอ

ฮั่นแน่ ชอบ{% include highlight-text.html content="ไฮไลท์" %}เหรอ

ฮั่นแน่ ชอบ{% include highlight-text.html content="ไฮไลท์" %}เหรอ
{%endraw%}
```

กด save แล้ว refresh ได้ผลลัพธ์เหมือนเดิม

![3](/blog/assets/img/2019/05/10/3.png)

เพิ่มเติมคือ ต่อไปถ้าอยากจะใส่ style หรือเขียนโค้ด html อะไรเพิ่มใน highlight text ก็ไม่ต้องไปใส่แก้ไฟล์ใน `_posts` ทุกไฟล์แล้ว แก้แค่ `_includes/highlight-text.html` ก็เพียงพอ

{% include focus-text.html content="ขออธิบายเพิ่มเติม"%}

```
{%raw%}{% include highlight-text.html content="ไฮไลท์" %}{%endraw%}
```

หมายถึงให้ include ไฟล์ที่ชื่อว่า `highlight-text.html` ที่อยู่ในโฟลเดอร์ `_includes` เข้ามาด้วย โดยส่งตัวแปรที่ชื่อว่า `content` มีค่าข้างในคือคำว่า `ไฮไลท์` เข้าไปแทนที่ `{%raw%}{{ include.content }}{%endraw%}` ที่อยู่ในไฟล์ `highlight-text.html` แล้ว Jekyll ก็ render โค้ดออกมาตามภาพด้านบนที่เราเห็นคำว่า <span style="color: #159957;">ไฮไลท์</span> เป็นสีเขียว

concept ของ component templates ใน Jekyll ก็ประมาณนี้

# แล้วเราจะเขียน component อะไรมาใช้ได้บ้างล่ะ?

โหยย บอกเลยว่าเยอะะะะมากกกกกกกก แล้วแต่ว่าเราจะรังสรรค์อะไร อยากให้มีอะไรในบล็อกของเราบ้าง

อย่างในบล็อกนี้ที่เห็นกันผ่านๆตาบ่อยๆก็เยอะแยะ เช่น

{% include focus-text.html content="อันนี้ที่นี่เรียก focus text" %}

{% include low-focus-text.html content="ส่วนนี่เป็น low focus text" %}

{% include file-name.html content="อันนี้เป็นชื่อไฟล์ข้างบนโค้ด" %}

{% include mrA.html content="dialog block คำพูดของ Mr.A" %}

{% include additional.html id="1" topic="ทำ panel เปิดปิดแบบนี้ได้ด้วย" 
    text="<p>ฮั่นแน่~</p>" %}

ทั้ง signature ด้านล่างทุก entry, สารบัญลิ้งด้วยบน, หรือลิ้งไปอ่าน EP อื่นใน series เดียวกันของบล็อกนี้ ก็ล้วนเขียนเป็น component ไว้ใน `_includes` ทั้งสิ้น {% include low-focus-text.html content="[เข้าไปดู sourcecode จิ้มจ้า](https://github.com/AimeTPGM/blog){:target='_blank'}" %}

คือมันแล้วแต่เราจะเขียนเลย อยากจะ advance แค่ไหนก็ได้หมด ลองเปิด Google ดู บางทีก็มีคนทำ Plugins เอาไว้ให้แล้ว

{% include low-focus-text.html content="โดยส่วนตัวแล้ว ชอบเขียนใช้เองมากกว่าพึ่ง Plugins เพราะว่าปลั้กอินบางตัว จะ customize อะไรก็ยาก หรืออาจจะหยุดซัพพอร์ตไปแล้ว ถ้าเราเขียนเอง เราย่อมรู้ว่าโค้ดของเราอยู่ตรงไหน ทำงานยังไง จะแก้อะไรก็สะดวกใจกว่า เลยชอบเขียนเอง แต่ถ้าปลั้กอินเพียบพร้อมมากๆ ก็จะเอามาใช้ เพราะขี้เกียจ 555" %}

ด้วยความที่มันเปิดบน Browser ได้ ก็สามารถเขียน javascript ลงไปได้ด้วย แค่ใส่ `<script type="text/javascript"></script>` ลงไปก็ใช้ javascript ได้แล้ว

ถ้าใครถนัด Angular, JQuery, React หรืออยากใช้ tools อื่นๆร่วมกับ Jekyll ก็ย่อมได้ แค่แอด library เข้ามาใน header ของหน้า `default.html` แล้วเขียนโค้ดลงไปตรงที่ต้องการก็จบ

# ก่อนจบเนื้อหาหลัก

สำหรับ series ทำ Blog ด้วย Jekyll ตั้งใจจะเขียนเนื้อหาหลักไว้แค่ 4 Parts ที่เหลือจะเป็น Spin-off หมดและ

ซึ่งใน Spin-off จะเน้นโค้ดสำหรับทำ component ต่างๆไว้ใช้, ทำ seo, ติด google analytic, ติด social media sharing หรืออะไรก็ตามที่นั่งทำๆไปแล้วคิดว่ามันเจ๋ง อยากให้มาอยู่ในบล็อก ไว้จะทยอยๆทำ แล้วตามอัพเดตนะคะ

ขอบคุณที่เข้ามาอ่านมากๆ หวังว่าจะเป็นประโยชน์และเริ่มเขียนบล็อกกันเองมากขึ้น

ขอให้สนุกกับการทำบล็อกและงมโค้ดค่ะ

สวัสดีค่ะ

{% include signature.html %}

