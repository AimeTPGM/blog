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
 - เข้าใจ Dependency Management
 - Maven vs Gradle
 - Before Started
 - Hello, World
 - Run Spring Boot
tags: [web, java, spring, maven]
---

![Spring Boot]()

# Spring Boot คืออะไรและทำไมต้อง Spring Boot

ขอเริ่มด้วยธรรมเนียมของบล็อก ก่อนจะเริ่มอะไรใหม่ๆ มาถามตัวเองกันก่อนว่า เรากำลังจะทำอะไร และทำไมเราถึงเลือกสิ่งนี้มาทำ

สำหรับคนที่กำลังมองหาเทคโนโลยี สำหรับทำ Web Service โดยพื้นฐานเขียน Java ได้อยู่แล้ว คงเคยได้ยินชื่อ Framework ตัวนี้จนชินหู ว่าแต่ มันคืออะไรล่ะ?

Spring Boot นั้น พัฒนามาจาก Spring ไม่ Boot #เดี๋ยวๆๆๆๆๆ 

นี่พูดจริง!

ก่อนหน้าที่จะมี Spring Boot เรามีเฟรมเวิร์คที่ชื่อว่า Spring อยู่แล้ว ซค่ง Spring ตัวนั้นจะต้องทำ Configuration เอง เช่น ต้องเขียน Java Bean เอง หรือแม้กระทั่งต้องรัน Tomcat เองอะไรเอง

แต่ Spring Boot เกิดมาเพื่อทำให้เราทำ Spring Application ได้ง่ายขึ้น เพราะ provide สิ่งที่ต้องใช้ทุกอย่างมาให้หมด! (เรียกว่าถึงขั้นสปอยล์เลยก็ได้)

ถ้าเปรียบเทียบให้เห็นภาพ Spring ก็เหมือนกับส่วนผสมต่างๆ ที่ต้องการเชฟมา mix มาทำกระบวนการวิธีใดๆ ให้ออกมาเป็นอาหารจานนึง

แต่ Spring Boot คือเหมือนกับอาหารที่ปรุงมาแล้ว เอาไปอุ่นใส่กระทะ เติมนู่นนิด นี่หน่อย ก็เสร็จ พร้อมทาน

Spring Boot เลยช่วยเข้ามาจัดการส่วนที่เราจะต้องทำซ้ำไปซ้ำมา เวลาสร้าง Application ขึ้นมาหนึ่งตัว แล้วก็ Simplified ให้มันใช้งานได้ขึ้นด้วย (เทียบกับ Spring ไม่ Boot) 

องค์กรที่เป็น Enterprise ก็ใช้ Java กันอย่างแพร่หลาย Spring Boot ก็เข้าไปแพร่พันธุ์งอกงามถึงระดับองค์กรกันเลยทีเดียว

และสำหรับคนที่เขียน Java อยู่แล้ว อยากลองเขียน Web Application แบบ MVC หรือ Backend API ไม่ว่าจะ RESTful หรือ SOAP Spring ก็มีให้ และหา material อ่านได้มากมายใน Google

นอกจากนี้ พอ build เสร็จจะได้ไฟล์ .jar เอาไปโยนลง server ที่รองรับ Java ก็รันได้หมดทุกที่ (หรือถ้าใครอยากได้ .war ก็มีให้เลือกเหมือนกัน)

ทั้งนี้ทั้งนั้น ถึง Spring Boot จะช่วยเราหลายๆอย่างแล้ว ประหยัดเวลาเขียนโค้ดไปได้เยอะแล้ว (เทียบกับ Spring) บางอย่างก็ยังมี Framework อื่น ที่ใช้ Programming Language อื่น ที่สามารถขึ้น App ได้รวดเร็วกว่า 

แต่วันนี้ขอมาขาย Spring Boot กันแบบ Zero to Hero จะพยายามอธิบายให้ลึกและเข้าใจง่ายที่สุดเท่าที่จะทำได้ละกันเนอะ

# เข้าใจ Dependency Management

เวลาเราเขียน Spring Boot Application เรามักจะดึง Library ตัวนั้น ตัวนี้มาใช้ ซึ่งในที่นี้เราเรียกว่า Dependency

ตัว Dependency ใน Spring ก็ไม่ต่างจาก Dependency ในที่อื่นๆ คือ เวอร์ชั่นของแต่ละ Dependency ต้อง compatible ซึ่งกันและกัน (ใช้ด้วยกันได้ ไปด้วยกันได้) 

ถึงจะ clean, build, complie, package, test, deploy ได้อย่างไม่มีปัญหาเรื่อง conflict จาก version ของ dependency

ดังนั้นจึงต้องมีการจัดการ Dependency (Dependency Management) โดยการใช้ Tools เข้ามาช่วย

ใน Spring Boot จะมี Dependency Management อยู่ 2 เจ้าคือ Maven กับ Gradle

# Maven vs Gradle

![Maven]()

Maven คือ ?

อย่างที่บอกไปด้านบน Maven เป็น Build Tools ที่ช่วยให้เราจัดการ dependency ได้ง่ายขึ้น เพราะมันมีคลังของ sourcecode จากที่ต่างๆ เก็บไว้เป็นของตัวเอง

หัวใจหลักของ maven คือ pom file ที่อยู่ในรูปของ xml (`pom.xml` น่ะแหล่ะ)

โดยเราสามารถกำหนด configuration ของ App เราได้ในตัว pom (เช่น artifactId, groupId, version, ฯลฯ) รวมถึง dependency ต่างๆที่เราจะเอามาใช้ 

เวลาเราสั่ง `mvn install` terminal ของเราจะไหลยาวเป็นพรืดๆ สังเกตดีๆ นั่นคือมันกำลังดาวน์โหลด dependency จาก maven มาใช้นั่นเอง

![Gradle]()

ส่วนน้อง Gradle คือ dependency management อีกตัวนึง คล้ายๆกับ Maven แหล่ะ แต่ใช้ Groovy ในการเขียน (Groovy เติบโตมาจาก Java) 

ซึ่งเอาจริงน้องอ่านง่ายและ clean กว่ามาก ปัจจุบันคนเริ่มหันมาใช้ Gradle เยอะขึ้นละ 

แต่ถ้าสังเกตดูดีๆ repository ของ Gradle ก็ยังเรียกใช้ sourcecode จาห maven central อยู่เลย

Blog series นี้จะขอใช้ Maven เป็นหลัก และถ้าจัดหาเวลาได้ จะเขียน Blog เกี่ยวกับ Maven แบบละเอียดแยกออกไปอีกทีนะคะ

แต่ถ้าใครอยากใช้ Gradle ก็ไม่ห้ามกัน เพราะ scope ที่จะพูดถึงคือทั้ง 2 tools นี้ครอบคลุมหมด เลือกใช้กันเอาตามสะดวก

# Before Started

ก่อนที่เราจะเริ่ม ขอรบกวนเวลาไป setup คอมกันนิดนึง โดยการติดตั้ง 3 อย่างในลิสต์นี้ลงคอมตัวเองด้วยค่ะ

- Java
- Maven
- IntelliJ

อย่าลืมเสร็จ JAVA_HOME หลังลง Java และ M2_HOME หลังลง Maven ใน system environment variable กันให้เรียบร้อย

เปิด IDE ขึ้นมา ในที่นี้ขอแนะนำให้ใช้ IntelliJ เพราะนาง powerful สุดๆ (ถ้าใครสะดวกจะใช้ Eclipse หรือ Spring Tool Suite ก็ไม่ว่ากัน แต่เชียร์ IntelliJ มากกว่านะ)

Setup เสร็จแล้ว ก็มาเริ่มกันเลย!

# Hello, World

วิธีง่ายสุดสำหรับการเริ่มโปรเจ็ค Spring ในยุคนี้คือเข้าเว็บ [https://start.spring.io/](https://start.spring.io/) ค่ะ

เข้าไปแล้วจะเจอเว็บหน้าตาแบบนี้

start.spring.io เป็นเว็บแอพ Official มาจาก Spring.io โดยตรง ซึ่งเราแค่กรอกๆลงไป ติ้กถูกเลือก dependency ที่เราอยากได้ (ซึ่งเป็น dependency ที่เค้าคัดมาแล้วว่าคนส่วนใหญ่ใช้) แล้วกด Generate Project ก็เป็นอันเสร็จ

ใครอยากสร้างทางลัด เสร็จไวๆ คลิ๊กอ่านในกล่องนี้

แต่แน่นอนว่า เว็บนี้เป็นเป็น Hardcore ง่ายๆไม่ ใหม่ๆชอบ เพราะเราเชื่อว่าการจะทำอะไรได้ให้ดี พื้นฐานต้องมี ความเข้าใจต้องปัง ดังนั้น 

มาเขียนเองกันค่ะ!!!

เปิด IntelliJ ขึ้นมา แล้วเลือก Create New Project

![Create New Project]()

เลือก Maven Project แล้วกด Next

![Maven]()

ใส่ GroupId กับ ArtifactId

GroupId คือ เรากำลังบอกว่าโค้ดของเราสำหรับโปรเจ็คนี้ อยู่ใต้กลุ่มนี้ 

ส่วน ArtifactId คือตั้งชื่อให้กับโค้ดส่วนนี้ที่เราจะเขียน

{% include additional.html id="2" topic="อ่านตัวอย่าง GroupId กับ ArtifactId" 
    text="<p>เช่น ถ้าเราจะทำโปรเจ็คสำหรับเว็บขายของเว็บนึงที่ชื่อ KaiKong เราอาจจะตั้งชื่อ GroupId ว่า com.myname.kaikong</p>
    <p>ส่วน ArtifactId อาจจะมี</p>
    <ul>
    <li>product เอาไว้ทำอะไรก็ตามเกี่ยวกับ product เช่น เก็บข้อมูล, แก้ข้อมูล, ลบข้อมูลของที่เราลงขาย</li>
    <li>order เอาไว้ทำอะไรก็ตามเกี่ยวกับ order เช่น เพิ่มออเดอร์ใหม่, แก้ไขข้อมูลออเดอร์</li>
    <li>user เอาไว้ทำอะไรก็ตามเกี่ยวกับ user เช่น จัดการข้อมูล user, login, register</li>
    </ul>" %}


ตั้งชื่อโปรเจ็ค แล้วกด Finish ได้เลย

จะได้โปรเจ็คเปล่าๆมาแบบนี้

ถ้าใช้ IntelliJ อย่าลืมกด Enable auto-import ที่ล่างขวามือด้วย 

มันเป็นการบอก IntelliJ ว่าให้ import dependency ให้อัตโนมัติ เวลาเราแก้อะไรใน pom.xml 

จากนั้นเปิด pom.xml ขึ้นมา