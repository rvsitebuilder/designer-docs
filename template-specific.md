### Template Specification Base

โครงสร้างสำหรับ Developer

## Structure

```text
        │ ├── resource/images/thumb-s.png
        │ ├── resource/images/thumb-m.png
        │ ├── resource/view/user/layouts/master.blade.php
        │ ├── resource/view/user/layouts/master-blank.blade.php
        │ ├── resource/view/user/layouts/layout1.blade.php
        │ ├── resource/view/user/layouts/layout2.blade.php
        │ ├── resource/view/user/layouts/layout3.blade.php
        │ ├── resource/view/user/layouts/layout4.blade.php
        │ ├── resource/view/user/partials/breadcrumbs.blade.php
        │ ├── resource/view/user/partials/userprofile???.blade.php
        │ ├── resource/view/user/header??
        │ ├── resource/view/user/alert.blade.php
        │ ├── resource/view/user/menu/top.blade.php
        │ ├── resource/view/user/menu/main-left.blade.php
        │ ├── resource/view/user/menu/main-right.blade.php
        │ ├── resource/view/user/menu/sidebar-left.blade.php
        │ ├── resource/view/user/menu/sidebar-right.blade.php
        │ ├── resource/view/user/menu/bottom.blade.php
        │ ├── resource/view/user/protected/sections/1.blade.php
        │ ├── resource/view/user/protected/sections/2.blade.php
        │ ├── resource/view/user/footer??

```
![DesignerDashboard](images/layout.jpg)


การตั้งชื่อ 
- css : ที่ใช้ในส่วนดีไซต์จะใช้ขีดกลาง(Kebab)  เช่น rv-name
- js : ที่ js เรียกใช้ เช่น class="js-name" หรือใช้แบบ attribute `<a data-editor="value"> test</a>` 
- ชื่อคลาส แบ่งส่วนประกอบ : จะใช้ เช่น id="selected-header", id="selected-footer"
- การเขียน Template blade variables เช่น {!! $templateSiteTitle !!} 
- editable_area คือ css กำหนดพื้นที่จุดที่สามารถเปลี่ยนแปลงได้( เปลี่ยนเป็น editable-area)
- js editmode : ที่ใช้เฉพาะส่วน edit mode เช่น app-name, editable_area, layoutfix โดยจะไม่ถูก publish
               โดยเปลี่ยนเป็นขีดกลาง(Kebab) เช่น class="js-xxxx-xxx"
- css editmode : ที่ใช้เฉพาะส่วน edit mode โดย css จะอยู่ในไฟล์ editor.css ไม่ถูก publish
                โดยเปลี่ยนเป็นขีดกลาง(Kebab) เช่น class="xxxx-xxxx-xxx"
- css editmode tool : ที่ใช้เฉพาะส่วน edit mode โดย css จะอยู่ในไฟล์ editor.css ไม่ถูก publish
                โดยเปลี่ยนเป็นขีดกลาง(Kebab) เช่น class="app-xxxx-xxx"
## Config

template.json ภายในมีอะไรบ้าง(ถ้าโปรแกรมเมอร์ปรับ เพิ่ม ให้มาปรับตรงนี้ด้วย)

```text
id : template_1
category_id : 1
description : Template เกี่ยวกับอะไร
version : 1.0
header : 1
footer : 1
menu : 1-main
topmenu : 1
use_sidebar : 1
theme : 1
use_form : true
banner : 1
pages : Home, About
theme : 1
 ```

 ## Image Thumbnail Preview
 - Name : ตั้งชื่อรูปตัวอย่างแท็มเพลต thumb-s.png, thumb-m.png 
 - Type of file : .png
 - Image Size : ไม่เกิน 200kb
 - Dimensions : 400 x auto (size m)

## Template

โครงสร้าง Master ประกอยด้วยตัวแปรและเลเอาท์ครอบนอกสุดมี ID และ Class ที่ใช้ในฝั่ง edit mode และ view mode 
ใช้โค้ด uikit3 

Master.blade.php

```html
<!DOCTYPE html>
<html lang="{{ app()->getLocale() }}">
  <head>
    {!! $head !!}  
  </head>

  <body id="app-layout">
    <div class="app-viewmode">

        <!-- เริ่ม Template Website สำหรับไฟล์ Template App Overwrite -->
        <div data-editor="editor" data-css="uikit3">
          <div class="rv-wrapper {{ $fullwidth }}">
            <div id="app">

              <header id="selected-header">
                   {!! $header !!}
              </header>

              <main id="selected-body">
                   {!! $layout !!}
              </main>

              <footer id="selected-footer">
                <div class="editable_area">
                    {!! $footer !!}
                </div>
              </footer>

           
              <div id="selected-navigator-mobile">
                   {!! $mobileMenu !!}
              </div>
        

          </div> <!-- End app -->
        </div> <!-- End rv-wrapper -->
      </div><!-- End data-editor -->
      
    </div><!-- End view-mode -->

    {!! $javaScript !!}  
    {!! $alert !!}

  </body>
</html>
```
@TODO: 
- app-viewmode: ชื่อเดิม bodyTemplate ย้ายไว้ด้านบน <div class="bodyTemplate"> เนื่องจากใช้ใน editmode อย่างเดียว มีผลให้ fullwidth พัง js เรียกลำดับคลาส selector ย้อนขึ้น ต้องแก้ใหม่โดยใช้ data-editor และ js เรียกใช้งานหลายที่กับเลเอาท์ฝั่ง edit mode สำหรับ css ใช้กับเมนูกลุ่ม Responsive Mode 
- {!! $head !!} : ให้ใส่เป็น Variable สำหรับโปรแกรมโค้ดที่อื่น เพื่อรองรับการ Overwrite
- {!! $javaScript !!} แทนค่าตำแหน่งที่วาง js css เพื่อรองรับการ Overwrite
- {!! $Layout !!} : เรียกไฟล์ layout1.blade.php, layout2.blade.php, layout3.blade.php, layout4.blade.php
- {!! $alert !!} : เรียกไฟล์ Notify มาแสดง เป็น absolute อยู่ส่วนใดก็ได้บนแท็มเพลต เรียกไฟล์ user/alert.blade.php
- app-layout : jsเรียกใช้งาน (/js/plugins/SiteTheme/init.js) 
- rv-wrapper : เดิม คือดีไซต์ uk-container uk-container-center
- app : คือ id="app" jsเรียกใช้งาน (assets/js/app.js) 
- {{ $fullwidth }} ใช้ในการตั้งค่า fullwidth ทั้งเว็บไซต์ ที่เมนู Design >> Website
- data-editor="editor" : ใช้งานกับ Editor WYS
- data-css="uikit3" :  ใช้งานกับ css framework อะไร
- #selected_body คือ มีเฉพาะ master มีผลตอนลากวาง(drag and drop) section 


## Head Tag

แท็กต่างๆ ที่อยู่ภายใน `<head>…..</head>`
Site Config , Favicon, css/js Component, css/js ของ RVsitebuilder, Theme/Custom


## Body Tag

เริ่มแท็ก `<body>…..</body>`
ภายในแสดง โครงสร้าง Template ประกอบด้วย `<header>..</header>, <main>..</main>, <footer>..</footer>` มี id #selected-header, #selected-body, #selected-footer, #selected-navigator-mobile อยู่ในแต่ละแท็ก

