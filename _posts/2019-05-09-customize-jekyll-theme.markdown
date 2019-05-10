---
layout: post 
series: ทำ Blog ด้วย Jekyll
series_episode: III
topic:  "แต่ง Blog สวยๆ ด้วย Jekyll Theme"
subtitle: "Blog ไป Code ไป สะใจจริงๆ"
createdDate:   2019-05-09 16:48 +0700
lastModifiedDate: 2019-05-10 11:45 +0700
categories: jekyll
tableOfContent:
 - Requirements
 - Start Using Jekyll Theme
 - ทำหน้า Homepage และ Blog Post
 - สร้างหน้า Home
 - สร้าง Blog Post
 - เข้าใจ Gem-based Theme
 - แก้ Theme Styling
tags: [web, blog, jekyll]
---
{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/09/thumbnail.png" %}

สำหรับคนที่เริ่มเขียน Blog แล้วอัพโหลดขึ้น Github ตาม [EP1](/blog/jekyll/2019/05/06/blog-like-a-coder.html){:target="_blank"} และ [EP2](/blog/jekyll/2019/05/08/jekyll-github-page.html){:target="_blank"} กันแล้ว

EP นี้เราจะมาแต่ง Blog จากการ Override Official Theme ของ Jekyll กัน!

{% include focus-text.html content="ทำไมต้อง Override?" %}

จริงๆแล้ว เราสามารถเขียน Jekyll Theme มาใช้เอง แบบ From Scratch ได้ 

แถมยัง Upload ให้คนอื่นเอา Theme เราไปใช้ได้ด้วย

แต่สำหรับ<del>คนขี้เกียจ</del>ผู้เริ่มต้น การเอา theme ที่มีอยู่แล้วมา Override จะช่วยให้เราประหยัดเวลาและเข้าใจวิธีการทำงานของ Jekyll ง่ายขึ้น ต่อไปอยากจะแต่ง อยากจะเอาอะไรลง Blog ก็สนุกไปหมด

{% include focus-text.html content="อย่างที่บอกไป EP แรก" %} 

{% include blog-quote.html content="Blog ไป Code ไป สะใจจริงๆ" %}

{% include focus-text.html content="<b>คำเตือน:</b>" %} entry นี้ค่อนข้างยาว เหมาะสำหรับอ่านไป ทำไปพร้อมๆกัน ทำเสร็จแล้วจะได้ blog พื้นฐานแบบสวยๆ เอาไปร่อนอวดคนอื่นได้เลย

# Entry นี้มีอะไรบ้าง

{% include table-of-content.html header=page.tableOfContent %}

# Requirements

- เอ็นทรี่นี้ไม่ขออะไรมาก นอกจากเวลา ใจที่อยากเรียนรู้และความอึดถึกทนของคนอ่าน
- อย่าลืม commit และ push code ขึ้น git ทุกครั้งที่ทำแต่ละ step เสร็จ Blog ของเราจะได้ publish ขึ้นอย่างต่อเนื่อง แถม revert code มาตรงจุดที่เราต้องการได้ด้วย

# Start Using Jekyll Theme

การแต่ง Theme ของ Jekyll ทำให้การเขียน Blog แบบเดฟๆ สนุกขึ้น 

ต่อจาก [EP2](/blog/jekyll/2019/05/08/jekyll-github-page.html){:target="_blank"} เปิด Github Repo ที่เราอัพโหลด Jekyll ขึ้นมา แล้วไปที่ `Setting`

![1](/blog/assets/img/2019/05/09/1.png)

เลื่อนลงไปที่ `Github Page` จะเห็นปุ่ม Change Theme จิ้มเลย

![2](/blog/assets/img/2019/05/09/2.png)

Github จะพาเราไปหน้านี้ เลือก theme ที่เราชอบ

![3](/blog/assets/img/2019/05/09/3.png)

ส่วนตัวเลือก theme {% include focus-text.html content="Cayman" %} เพราะว่าดูคลีนๆดี ไม่รกมาก และน่าจะแต่งเพิ่มง่าย 

ตัดสินใจได้แล้วก็จิ้มปุ่ม Select Theme เขียวๆด้านซ้ายมือ

กลับไปที่ Github Repo เลือก Commit

![4](/blog/assets/img/2019/05/09/4.png)

จะเห็นว่ามี commit ใหม่เกิดขึ้นในชื่อเราว่า `Set theme jekyll-theme-cayman`

![5](/blog/assets/img/2019/05/09/5.png)

แปลว่าเรา apply theme Cayman กับ Blog ของเราแล้วเรียบร้อย

{% include focus-text.html content="__เพิ่มเติม__" %} ถ้าลองไปดูที่ `_config.yml` จะมี `theme: jekyll-theme-cayman` ซึ่งเป็นการบอก jekyll เวลารัน/บันเดิลว่าเราเอา theme Cayman มาใช้

{% include additional.html id="1" topic="สำหรับคนที่ต้องการใช้ non-official theme จาก opensource บน Github" 
    text="<p>ถ้าไปเจอ theme jekyll สวยๆบน Github repo ของใครสักคน แล้วอยากเอามาใช้ ให้ลบ <em>theme: sometheme</em> ออก แล้วเปลี่ยนเป็น <em>remote_theme: someone/theme-repo-name</em></p> <p>ลองอ่านไฟล์ Readme ของ Github repo นั้นดู ปกติเค้าจะเขียนอธิบายไว้ว่าต้อง setup ยังไง ถึงจะใช้ theme เค้าได้</p>" %}

เปิด cmd หรือ Terminal ของเราขึ้นมา change directory ไปที่ blog แล้วรันคำสั่ง

```
$ git pull origin master                 # pull code ล่าสุดจาก master branch
$ bundle exec jekyll serve --watch       # รัน jekyll server และให้ hot reload ทุกครั้งที่ save
```
เปิด Browser ไปที่ `localhost:4000/blog/` แล้วก็จะพบว่า ...

![6](/blog/assets/img/2019/05/09/6.png)

{% include focus-text-lvl1.html content="หน้าว่างเฉยเลยว้อยยยยยย" %} 

ทำไม ทำไม ทำไม ทำไม ทำมายยยยยยยย ?????????

ไม่ต้องแพนิคและแอบงง เพราะนี่งงมาก่อนแล้ว เดี๋ยวจะอธิบายในหัวข้้อต่อไป

# ทำหน้า Homepage และ Blog Post

ที่หน้าแรกมันว่างเปล่าเพราะ ??? เคยเกริ่นไปใน [EP1](/blog/jekyll/2019/05/06/blog-like-a-coder.html){:target="_blank"} ว่า 

{% include blog-quote.html content="หน้าแรกของเพจจะเริ่มต้นอ่านที่ <em>index.md</em> เสมอ" %}

โอเค งั้นเราเปิด `index.md` ขึ้นมาดูกัน จะเจอแบบนี้

{% include file-name.html content="index.md" %} 
```html
---
layout: home        # แปลว่าเรียกใช้ home.html
---

<!-- ตรงนี้เอาไว้ใส่ content ของหน้า home ได้ 
แล้วเรียกใช้ {% raw %}{{ content }}{% endraw %} ใน home.html -->
```

เนื่องจากเราเลือกใช้ theme Cayman เราต้องไปดูก่อนว่า Cayman นั้นเขียนหน้า `home.html` ไว้อย่างไร ทำไมมันถึงว่างเปล่า

ใครอ่านถึงตรงนี้ ขอเชิญเข้าไปสำรวจ [Github ของ Cayman (จิ้มเลยจ้า)](https://github.com/pages-themes/cayman){:target="_blank"} ไปพร้อมๆกัน

เข้าไปที่ `_layouts` จะเห็นว่า

![7](/blog/assets/img/2019/05/09/7.png)

{% include focus-text-lvl1.html content="Cayman ไม่มี code สำหรับหน้า Home" %} 

แว๊บแรกที่เห็นคือ .. วดฟ แล้วฉันจะทำยังไง

เราหาคำตอบมาให้แล้ว ใน section หน้า แต่อยากให้ลองทำหน้า Home กันต่อไปอีกสักนิดนึง

{% include focus-text.html content="ไม่มีหน้า home ใช่ไหม? ก็สร้างเองเลยสิ!" %}

## สร้างหน้า Home

กลับมาที่ text editor ของเรา ไปที่โฟลเดอร์ `_layouts` (ถ้าไม่มีก็สร้างโฟลเดอร์เองเลย) แล้วสร้างไฟล์ `home.html` เปล่าๆ ไว้

```
~/blog/
│   _config.yml        
|   .          
│   . ไฟล์ต่างๆ  
│   .                       
│
└─── _posts/
|
└─── _layouts/       <<<<< โฟลเดอร์ตรงนี้
    │   home.html    <<<<< เอาไฟล์ home.html ไว้ตรงนี้
```

จากนั้นเปิดไฟล์ `home.html` ขึ้นมา เขียนโค้ดลงไปประมาณนี้

{% include file-name.html content="_layouts/home.html" %} 
```html
---
layout: default         # extends มาจากหน้า default
---

<!-- เดี๋ยวเราจะใส่ content หน้า home กันตรงนี้ -->
```

ใส่แล้วสั่งรัน `bundle exec jekyll serve` กันเลย

เปิด Browser ขึ้นมา แล้วไปที่ `localhost:4000/blog/` บล็อกของเรามี header กับ footer ขึ้นมาแล้ว!

![8](/blog/assets/img/2019/05/09/8.png)

ซึ่งเป็นผลมาจากที่เราเอา `layout: default` เข้ามานั่นเอง {% include low-focus-text.html content="[เข้าไปดูโค้ดหน้า default.html ของ Cayman Theme จิ้ม](https://github.com/pages-themes/cayman/blob/master/_layouts/default.html){:target='_blank'}" %}

{% include additional.html id="4" topic="ถ้าเจอ Error: theme could not be found" 
    text="<p>เปิด `Gemfile` ขึ้นมา make sure ว่าเรามี dependency ตัวใดตัวหนึ่งด้านล่างนี้</p>
    <pre>gem 'github-pages', group: :jekyll_plugins</pre>
    <p>หรือ</p>
    <pre>gem 'jekyll-theme-cayman'</pre>
    <p>ปกติ theme cayman จะมากับ dependency <em>github-pages</em> อยู่แล้ว ดังนั้นมีแค่อันบนก็เพียงพอครอบคลุมจักรวาล Jekyll official theme จ้า</p>" %}

{% include focus-text.html content="แต่ยังไม่เห็นมีลิสต์ของ entry ขึ้นมาเลย?" %}

มาโค้ดด้วยกันต่อที่ `_layouts/home.html` (หน้าเดิม)

{% include file-name.html content="_layouts/home.html" %} 
```html
---
layout: default         # extends มาจากหน้า default
---
{% raw %}
<!-- เพิ่มโค้ดข้างล่างนี้ -->
<div>

    <!-- วน loop ทุก posts ในเว็บเรา -->
    {% for post in site.posts %}  

    <div>

        <!-- สร้าง link ไปที่ post -->
        <a href="{{ post.url | relative_url }}">    

            <!-- เอาชื่อ title มาจาก post -->
            {{ post.title }}             
        </a>         
    </div>

    <!-- จบ loop -->
    {% endfor %}

</div>
{% endraw %}
```

กลับไปที่ Browser กด refresh หนึ่งที มี Blog entry ขึ้นมาแล้ว!! (เย้)

![9](/blog/assets/img/2019/05/09/9.png)

link ของแต่ละ entry กดได้ด้วย! แต่ ...

![10](/blog/assets/img/2019/05/09/10.png)

{% include focus-text-lvl1.html content="หน้า Blog ไม่เห็นสวยเลยยย T^T อะไรอีกเนี่ยยย" %}

ลองเข้าไปอ่าน [Jekyll's official document about Post](https://jekyllrb.com/docs/posts/){:target="_blank"} เค้าบอกว่า

{% include blog-quote.html content="All blog post files must begin with front matter which is typically used to set a layout or other meta data." %}

{% include blog-quote.html content="ไฟล์ blog ทุกๆไฟล์ จะต้องเริ่มต้นด้วย front matter ที่เอาไว้เซ็ต layout หรือค่าอื่นๆในหน้านั้น" %}

อ่ะ ลองเปิดไฟล์ใน `_posts` ขึ้นมาดูสักไฟล์นึง

{% include file-name.html content="_posts/2019-05-06-welcome-to-jekyll.markdown" %} 
```html
---                                         # ตรงนี้แหล่ะที่เรียกว่า front matter
layout: post                                # บอกว่าใช้ layout อะไร (ในที่นี้คือ post.html)
title:  "Welcome to Jekyll!"                # metadata สำหรับชื่อ entry
date:   2019-05-06 18:33:25 +0700           # metadata สำหรับวันที่เขียนบล็อก
categories: jekyll update                   # metadata สำหรับหมวดหมู่ของบล็อก
---                                         # จบ front matter บรรทัดหลังจากนี้คือ content ใน blog นั้น

You’ll find this post in your `_posts` directory.
.
.
<--  content ยาวๆ -->
.
.
```

{% include focus-text.html content="แปลว่า blog post ทุกอันใช้ <em>layout: post</em> ซึ่งมาจากไฟล์ <em>_layouts/post.html</em>" %}

ตะกี้ ตอน [สร้างหน้า Home](#สร้างหน้า-home) เราแอบเข้าไปดูโค้ดในโฟลเดอร์ `_layouts` ของ theme Cayman แล้วเห็นว่ามันมีแต่โค้ด `default.html` อย่างเดียว

{% include focus-text.html content="แสดงว่าโค้ดสำหรับหน้า Post ก็ไม่มี! omggggg" %}

## สร้าง Blog Post

ถ้าไม่มี งั้นเรามาสร้างหน้า blog post แบบง่ายๆสวยๆกัน

{% include focus-text.html content="คอนเซ็ปเดิม ถ้าไม่มี ก็สร้างเองเลย" %}

เริ่มจากสร้างไฟล์ `post.html` ไว้ในโฟลเดอร์ `_layouts` แบบนี้

```
~/blog/
│   _config.yml        
|   .          
│   . ไฟล์ต่างๆ  
│   .                       
│
└─── _posts/
|
└─── _layouts/       
    |   home.html
    │   post.html     <<<<< สร้างอันนี้เพิ่ม
```

ใส่โค้ดของหน้า post ลงไป

{% include file-name.html content="_layouts/post.html" %} 
```html
---
layout: default         # ตรงนี้จะเอา header กับ footer เข้ามาเหมือนหน้า home
---
{% raw %}
<div>
    <!-- ตรงนี้จะ render content ของไฟล์ .markdown ที่ใช้ layout: post ในโฟลเดอร์ _post  -->
    {{content}}
</div>
{% endraw %}
```

กด save แล้ว refresh browser หนึ่งที

![11](/blog/assets/img/2019/05/09/11.png)

{% include focus-text-lvl1.html content="มาแล้ว!! Blog สุดสวยของเราาา" %}

ถ้าอยากเพิ่ม link สำหรับกลับมาหน้า Home เพิ่มโค้ดลงไปแบบข้างล่างนี่

{% include file-name.html content="_layouts/post.html" %} 
```html
---
layout: default         # ตรงนี้จะเอา header กับ footer เข้ามาเหมือนหน้า home
---
{% raw %}
<div>
    {{content}}
</div>

<!-- เพิ่มโค้ดนี้จ้า  -->
<a href="{{ site.baseurl }}">back to home</a>
{% endraw %}
```

save แล้ว refresh ก็ได้ลิ้งกลับไปหน้า home แล้ววว

![12](/blog/assets/img/2019/05/09/12.png)

เท่านี้แหล่ะ วิธีการสร้าง layout template สำหรับใช้ใน Jekyll 

# เข้าใจ Gem-based Theme

{% include focus-text.html content="จาก section hardcore coding เมื่อกี้ ขอเอามาสรุปเป็นข้อๆ" %}
1. ถ้าเจอ front matter แล้วเห็นคำว่า layout แปลว่าไฟล์นั้นๆ เป็น extends มาจาก `_layouts/layout_name.html` เสมอ
2. ถ้าหาโค้ด `layout_name.html` นั้นไม่เจอในโค้ดของเรา ให้ไปเปิดโค้ดของ theme นั้นๆใน github repo แล้วหาดูว่าเค้ามีรึเปล่า (โดยปกติแล้วโค้ด layout มันอยู่ใน theme ที่เราไปเอามานั่นแหล่ะ)
3. ถ้าที่ theme repo ก็ไม่มี สร้างขึ้นมาเองไปเลย 
4. Jekyll จะดูโค้ดที่ repo ของเราเป็นหลัก ถ้ามันหาไม่เจอ ถึงจะค่อยไปหาดูที่ theme repo ถ้าไม่เจออีก ก็จะโชว์หน้า blank blank หรือ โชว์เฉพาะส่วนของ content หลัง front matter นั่นแหล่ะ ถ้าอยากได้สวยๆ คือต้องมี code html layout

{% include focus-text.html content="นอกเหนือจากที่เราลอง code กันเมื่อกี้" %}

1. นอกจากเรื่อง `_layouts` และ `_posts` โครงสร้างของ Jekyll ยังมีโฟลเดอร์อื่นๆอยู่อีก หลักๆคือ `assets` และ `_includes` ที่อยู่ใน root folder เหมือนกัน (ในที่นี้คือ `~/blog/`)
2. `assets` คือโฟลเดอร์ที่เอาไว้เก็บ static file ต่างๆ อย่างรูปภาพ รวมถึงไฟล์ style ที่เอาไว้ customize blog อย่าง scss ด้วย หากอยากแก้ style ของเพจให้อ่าน section ต่อไป
3. ส่วน `_includes` เอาไว้เก็บ html components ต่างๆ ที่เราสามารถนำมา reuse ได้ (จะมาเขียนบล็อกแยกออกไปทีหลัง)

{% include low-focus-text.html content="[อ่านเพิ่มเติมเกี่ยวกับ Jekyll Theme จิ้มจ้า](https://jekyllrb.com/docs/themes/){:target='_blank'}" %}

# แก้ Theme Styling

สร้างโฟลเดอร์เพิ่มขึ้นมาอีกโฟลเดอร์นึงชื่อ `assets` ข้างในมีโฟลเดอร์ชื่อ `css` และไฟล์ `style.scss` แบบนี้

```
~/blog/
│   _config.yml        
|   .          
│   . ไฟล์ต่างๆ  
│   .                       
│
└─── _posts/
|
└─── _layouts/   
|   
└─── assets/   
    |
    └─── css/ 
        |
        └─── style.scss       
```

เปิดไฟล์ `style.scss` ขึ้นมา ใส่โค้ดตามนี้ เพื่อเป็นการ import scss มาจาก theme cayman

{% include file-name.html content="assets/css/style.scss" %} 
```html
---
---

@import 'jekyll-theme-cayman';
```

จากนั้น ลองไปดูว่ามี style ตรงไหนที่เราอยากเปลี่ยนบ้าง เช่น อยากเปลี่ยนสีตัวอักษรที่ title ของเพจให้เป็นสีเหลือง ก็ไปที่ browser > คลิ๊กขวา > inspect element > แล้วหาโค้ด title ของเพจให้เจอใน html

![13](/blog/assets/img/2019/05/09/13.png)

ตามรูป สังเกตโค้ดนี้

```html
<h1 class="project-name">title ของเพจ</h1>
```

แปลว่าที่ title ของเพจใช้ class ชื่อ project-name เราก็ไปเพิ่มในไฟล์ style.scss ของเราแบบนี้

```html
---
---

@import 'jekyll-theme-cayman';

.project-name {
    color: yellow;
}
```

save แล้วกด refresh

![14](/blog/assets/img/2019/05/09/14.png)

{% include focus-text-lvl1.html content="สำเร็จ! ข้อความ header เป็นสีเหลืองแล้ววว" %}

ถ้าเราอยากจะเปลี่ยน อยากจะเพิ่ม อยากจะลดอะไร ที่เป็น styling ก็ใช้วิธีนี้เปลี่ยนไปทีละจุด ทีละจุด จนกว่าเราจะพอใจ แล้วก็ push โค้ดขึ้น github ได้เลย github จะ deploy เว็บให้เราอัตโนมัติ

{% include focus-text.html content="แต่ถ้าอยากเปลี่ยน layout ของหน้าเว็บไปเลย" %} แนะนำให้สร้างไฟล์ `default.html` ลงในโฟลเดอร์ `_layouts` แล้วค่อยๆเขียนโค้ด html กับ css (หรือ scss) แบบที่เราออกแบบลงไป ก็เป็นอันเสร็จพิธี

# ก่อนจบ Entry

ใครที่อยากต่อยอดเว็บโดยการสร้างหน้าใหม่ๆ ให้ลองเริ่มจากไฟล์ `about.md` ที่มีอยู่ สร้าง `layout: page` (`_layouts/page.html`) แบบที่เราชอบ รัน jekyll แล้วลองเปิด localhost:4001/blog/about/ ดู

{% include file-name.html content="about.md" %} 
```html
---
layout: page
title: About
permalink: /about/
---

เกี่ยวกับเรา
```
ค่อยๆทำไปเรื่อยๆ ทำความเข้าใจกับโค้ดที่เราเขียน แล้วจะเจอว่า jekyll มีอะไรให้เล่นอีกเยอะ

ใครอ่านมาถึงตรงนี้ ปรบมือให้ตัวเองดังๆ คุณเก่งมาก (และอดทนมาก 5555)

Part นี้เป็น Part ที่เขียนเหนื่อยสุด แต่ตั้งใจเขียนมากสุด

หวังว่าจะเป็นประโยชน์กับใครหลายๆคนที่อยากเริ่มเขียน Blog ทำ Blog ของตัวเอง

ไว้มาเขียน Spin Off สั้นๆ เป็นโค้ดไว้ทำ components หรือหน้า page, tags, series, วิธีการใส่ seo, google analytic ฯลฯ

ขอจบ Entry นี้ไว้แค่นี้ 

สวัสดีค่ะ

{% include signature.html %}

