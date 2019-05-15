---
layout: post 
series: ทำ Blog ด้วย Jekyll
series_episode: Spin-off
topic:  "Jekyll: ทำ Pagination ที่หน้า Home"
subtitle: "บล็อกเริ่มเยอะ แบ่งย่อยๆเป็นหน้าๆละกัน"
createdDate:   2019-05-14 17:53 +0700
lastModifiedDate: 2019-05-14 19:12 +0700
categories: jekyll
tableOfContent:
 - Requirements
 - ทำ Pagination
tags: [web, blog, jekyll]
---

{% include hidden-thumbnail.html image="/blog/assets/img/2019/05/14/thumbnail.png" %}

พอเราสร้าง blog post ไปเรื่อยๆ หน้า home จะโชว์ list ยาวววววววววววววมาก

วันนี้เราจะมาลองทำ pagination ไว้แบ่งบล็อกเป็นหน้าๆกัน แบบนี้ 

![1](/blog/assets/img/2019/05/14/1.png)

กดเลขหน้า หรือ กดซ้ายขวาได้ด้วย

# Requirements

- มี Jekyll Blog

# ทำ Pagination

จริงๆแล้ว Pagination Plugins ของ jekyll ที่ใช้กันแพร่หลายมีอยู่ 2 เวอร์ชั่น คือ แบบ Official ([Jekyll Pagination](https://jekyllrb.com/docs/pagination/)) กับ v2 ([jekyll-pagination-v2](https://github.com/sverrirs/jekyll-paginate-v2))

ปกติ Jekyll Pagination จะมาพร้อมกับ Jekyll อยู่แล้ว 

ส่วน <u>jekyll-pagination-v2 ไม่ซัพพอร์ต Github Page</u> เราเลยจะใช้ pagination ที่มากับ Jekyll Official แทน

ถ้าใคร deploy jekyll ลงที่อื่น สามารถใช้ jekyll-pagination-v2 ได้นะคะ มี options ให้เล่นเยอะกว่าด้วย

เริ่มกัน

1. เปิด Jekyll Blog ขึ้นมา
2. ไปที่ไฟล์ `_config.yml` แล้วเพิ่ม configuration ด้านล่างลงไป
   ```
   paginate: 4                  # จำนวน Blog Post ต่อ 1 หน้า
   paginate_path: /page:num     # path สำหรับไปหน้า 1,2,3,4, ...
   ```
3. เปลี่ยนไฟล์ `index.md` ให้เป็น `index.html` เพราะ ตาม [document](https://jekyllrb.com/docs/pagination/) แล้ว {% include focus-text.html content="Jekyll pagination ใช้ได้กับ <em>index.html</em> เท่านั้น" %} 
   ```
   ~/blog/
    |   _config.yml   
    |   index.html            <<<<< เปลี่ยน index.md เป็น index.html เลย            
    |   .          
    |   . ไฟล์ต่างๆ  
    |   .                       
    |
    └─── _posts/
    ```

ลองเปิด `index.html` ดู จะเห็นว่าใช้ layout มาจาก home (ถ้าใครใช้ layout อื่น ก็เปิด layout html ของไฟล์นั้นนะ)
```html
---
layout: home     # ใช้ layout home จาก ~/_layouts/home.html
---
```

เปิดไฟล์ layout นั้นขึ้นมา แล้วเปลี่ยน `site.posts` ทุกๆที่ ให้ไปใช้ `paginator.posts` แทน เช่น

```html
{% raw %}
{% for post in site.posts %}
<!-- โค้ด html ต่างๆ ที่เอาไว้โชว์ post -->
{% endfor %}
{% endraw %}
```

เปลี่ยนเป็น

```html
{% raw %}
{% for post in paginator.posts %}
<!-- โค้ด html ต่างๆ ที่เอาไว้โชว์ post -->
{% endfor %}
{% endraw %}
```

save แล้วสั่งรัน `bundle exec jekyll serve` ที่หน้า home ก็จะเหลือแค่ 5 post ตามที่เราใส่ไว้ใน `_config.yml` ว่า `paginate: 5`

แล้วเพิ่มโค้ดสำหรับ pagination ไว้ด้านล่างของไฟล์

(ส่วนตัวทำเป็น component ไว้ใน `_includes` แล้วค่อย `{%raw%}{% include %}{%endraw%}` เข้ามา) 

```html
{%raw%}
<!-- ถ้า total page มากกว่า 1 ถึงจะโชว์ จำนวนหน้า -->
{% if paginator.total_pages > 1 %}
<ul style="display: flex; padding: 10px; justify-content: center;">
  <!-- ถ้ามี previous page ถึงจะโชว์ลูกศรไปด้านหน้า -->
  {% if paginator.previous_page %}
  <li style="padding-right: 20px; border-right: #eff0f1 1px solid">
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: ':num', page }}">
      <i class="fa fa-chevron-left"></i>
    </a>
  </li>
  {% endif %}

  <!-- วน for ตั้งแต่หน้า 1 ถึง total page เพื่อสร้างเลขหน้าเพจ -->
  {% for page in (1..paginator.total_pages) %}
  <li style="padding: 0 20px;">

    <!-- ถ้าเป็นหน้าแรก ให้โชว์บล็อก -->    
    {% if page == 1 %}
    <a href="{{site.baseurl}}/">{{ page }}</a>

    <!-- ถ้าเป็นหน้าอื่น ให้ไปที่ /blog/page2, /blog/page3, /blog/page4, ...  -->  
    <!-- อันนี้คือ active page ใส่ style ตามใจชอบ -->  
    {% else if page == paginator.page %}
    <!-- replace :num ด้วยเลข page -->    
    <a href="{{ site.paginate_path | prepend: site.baseurl | replace: ':num', page }}">{{ page }}</a>
    {% else %}
    <!-- อันนี้คือหน้าอื่นๆ -->  
    <a href="{{ site.paginate_path | prepend: site.baseurl | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
  </li>
  {% endfor %}

  <!-- ถ้ามี previous page ถึงจะโชว์ลูกศรไปด้านหลัง -->
  {% if paginator.next_page %}
  <li style="padding-left: 20px; border-left: #eff0f1 1px solid">
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: ':num', page }}">
      <i class="fa fa-chevron-right"></i>
    </a>
  </li>
  {% endif %}
</ul>
{% endif %}
{%endraw%}
```

กด save กลับไปดู `localhost:4000/blog/` มี pagination ขึ้นมาแว้ววว

![2](/blog/assets/img/2019/05/14/2.png)

ไว้เจอกันใหม่บล็อกหน้าค่า

{% include signature.html %}