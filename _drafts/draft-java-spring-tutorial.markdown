---
layout: post 
series: Spring Boot Zero to Hero
series_episode: I
topic:  "เริ่มต้นกับ Spring Boot"
subtitle: "มาทำ Restful Web Service ด้วย Spring Boot กัน"
createdDate:   2019-05-14 12:06 +0700
lastModifiedDate: 2019-05-07 11:30 +0700
categories: java spring
tableOfContent:
 - Spring Boot คืออะไรและทำไมต้อง Spring Boot
 - ส่วนประกอบของการสร้าง Spring Boot Application
 - Dependency Management
 - Before Started
 - Hello, World
 - Run Spring Boot
tags: [web, java, spring, maven]
---

# Spring Boot คืออะไรและทำไมต้อง Spring Boot

ขอเริ่มด้วยธรรมเนียมของบล็อก ก่อนจะเริ่มอะไรใหม่ๆ มาถามตัวเองกันก่อนว่า เรากำลังจะทำอะไร และทำไมเราถึงเลือกสิ่งนี้มาทำ

สำหรับคนที่กำลังมองหาเทคโนโลยี สำหรับทำ Web Service โดยพื้นฐานเขียน Java ได้อยู่แล้ว คงเคยได้ยินชื่อ Framework ตัวนี้จนชินหู ว่าแต่ มันคืออะไรล่ะ?

Spring Boot นั้น พัฒนามาจาก Spring ไม่ Boot #เดี๋ยวๆๆๆๆๆ 

นี่พูดจริง!

ก่อนหน้าที่จะมี Spring Boot เรามีเฟรมเวิร์คที่ชื่อว่า Spring อยู่แล้ว ซค่ง Spring ตัวนั้นจะต้องทำ Data Binding เอง 