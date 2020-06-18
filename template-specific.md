### Template Specification Developer

- พาธในโปรแกรม

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
- js : ที่ js เรียกใช้ เช่น js-name
- css แบ่งส่วนประกอบ : จะใช้ เช่น id="selected-header, id="selected-footer
- การเขียน Template blade variables เช่น {!! $templateSiteTitle !!} 
- editable_area คือ css กำหนดพื้นที่จุดที่สามารถเปลี่ยนแปลงได้
- js editmode : ที่ใช้เฉพาะส่วน edit mode เช่น app-name, editable_area, layoutfix โดยจะไม่ถูก publish
               โดยเปลี่ยนเป็นขีดกลาง(Kebab) เช่น js-xxxx-xxx
- css editmode : ที่ใช้เฉพาะส่วน edit mode โดย css จะอยู่ในไฟล์ editor.css ไม่ถูก publish
                โดยเปลี่ยนเป็นขีดกลาง(Kebab) เช่น xxxx-xxxx-xxx
- css editmode tool : ที่ใช้เฉพาะส่วน edit mode โดย css จะอยู่ในไฟล์ editor.css ไม่ถูก publish
                โดยเปลี่ยนเป็นขีดกลาง(Kebab) เช่น app-xxxx-xxx
## Config

template.json ภายในมีอะไรบ้าง

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
 - Dimensios : 400 x auto (size m)

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

              <!-- Navigation Mobile Compatible view-->
              <div id="selected-navigator-mobile">
                   {!! $mobileMenu !!}
              </div>
              <!-- End Navigation Mobile Compatible view-->

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
- {!! $alert !!} : เรียกไฟล์ Notify มาแสดง เป็น absolute อยู่ส่วนใดก็ได้บนแท็มเพลต
- app-layout : jsเรียกใช้งาน (/js/plugins/SiteTheme/init.js) 
- rv-wrapper : เดิม คือดีไซต์ uk-container uk-container-center
- app : คือ id="app" jsเรียกใช้งาน (assets/js/app.js) 
- {{ $fullwidth }} ใช้ในการตั้งค่า fullwidth ทั้งเว็บไซต์ ที่เมนู Design >> Website
- data-editor="editor" : ใช้งานกับ Editor WYS
- data-css="uikit3" :  ใช้งานกับ css framework อะไร
- #selected_body คือ มีเฉพาะ master มีผลตอนลากวาง(drag and drop) section 

## Layout (Left Sidebar / Page Content / Right Sidebar)
ใช้โค้ด uikit3 ภายในไฟล์นี้ กำหนดตำแหน่งเพื่อเรียกไฟล์อื่นๆ

layout1.blade.php

```html
<div class="uk-container uk-container-center">
  <!-- Set Sidebar delete rv-block-full -->
  <!-- Set Row Full width must use class of Design block -->
  <div class="uk-grid">
		<div class="uk-width-large-1-4 design-block sidebar-left" rv-layout="25" style="display: none;">
      <div class="layoutfix">
        <aside>
          <section>
            <div id="editable_area_content1" class="editable_area designBlock">
              
              {!! $menuSidebarLeft!!}
              <!--sidebar-right.blade.php -->

              {!! $sidebarLeftTemplate !!}
              <!-- (lib/Tempalte/Template.php มีโค้ด uikit อยู่) -->

              {!! $sidebarSection !!}

            </div>
          </section>
        </aside>
      </div>
    </div>

    <div class="uk-width-large-3-4 design-block sidebar-center" rv-layout="100">
      <div class="layoutfix">
        <div id="editable_area_content" class="editable_area designBlock">
          
          {!! $breadcrumbs!!} 

          {!! $contentSections!!}


        </div>
      </div>
    </div>

    <div class="uk-width-large-1-4 design-block sidebar-right" rv-layout="25" style="display: none;">
      <div class="layoutfix">
        <aside>
          <section>
            <div id="editable_area_content2" class="editable_area designBlock">
              {!! $menuSidebarRight !!}
              <!--sidebar-right.blade.php -->

              {!! $sidebarRightTemplate !!}
              <!-- เดิม มาจาก (lib/Tempalte/Template.php) -->

              {!! $sidebarSection !!}
              <!-- เรียก Sidebar Section (protected/sidebars/1.blade.php) -->
            </div>
          </section>
        </aside>
      </div>
    </div>
  </div>
</div>
```

@TODO: 
- designBlock: js เรียกใช้หลายที่ ส่วนใหญ่ใช้ใน edit mode
- layoutfix: js เรียกใช้หลายที่ ส่วนใหญ่ใช้ใน edit mode
- เดิม id="editable_area_content" ใช้ทั้ง js และดีไซต์ใน edit mode
- {!! $menuSidebarLeft!}  เรียกจาก menu/sidebar-left.blade.php
- {!! $menuSidebarRight!}  เรียกจาก menu/sidebar-right.blade.php
- {!! $Navigation!}  เรียกจาก menu/sidebar-left.blade.php
- {!! $sidebarLeftTemplate !!} เรียกจาก (lib/Tempalte/Template.php)
- {!! $sidebarRightTemplate !!} เรียกจาก (lib/Tempalte/Template.php)
- {!! $contentSection!!}  เรียกจาก (protected/sections/1.blade.php)
- {!! $sidebarSection !!} เรียกจาก (protected/sidebars/1.blade.php)


## Head Tag

แท็กต่างๆ ที่อยู่ภายใน `<head>…..</head>`
Site Config , Favicon, css/js Component, css/js ของ RVsitebuilder, Theme/Custom


## Body Tag

เริ่มแท็ก `<body>…..</body>`
ภายในแสดง โครงสร้าง Template ประกอบด้วย `<header>..</header>, <main>..</main>, <footer>..</footer>` มี id #selected-header, #selected-body, #selected-footer, #selected-navigator-mobile อยู่ในแต่ละแท็ก


## Header

การทำงาน เรียงสลับกันได้,กำหนด overlap, ซ่อน Banner ได้เหมือนเดิม

header.blade.php

```html
<div class="selected_overlap {{ class-design }}">
    top.blade.php
    menu.blade.php (menus/main-left.blade.php), (menus/main-right.blade.php)
    banner.blade.php
</div>
```
@TODO: 
- {{ class-design }} : คือจากแท็มเพลตดีไซต์แบบกำหนดเมนู Overlap กับแบนเนอร์ ต้องใส่คำว่า Overlap


## Top menu

Topmenu การทำงานเหมือนเดิม แต่ในดีไซต์เปลี่ยน css เป็นแบบใหม่ ตัวแปรยังคงเหมือนคือ [[LOGO]], [[TEL]], [[TOP_NAV]] มีเลเอาท์หลายดีไซต์
เพิ่มเติม: ซ่อนแถบ topmenu ได้

top.blade.php

```html
<section id="selected_topmenu">
    <nav>
        .....

    </nav>
  </section>
```

## Navigation
การวางตำแหน่งจุดต่างๆ
1. top
2. menu
3. left sidebar
4. right sidebar
5. bottom

เช่น
menu.blade.php

```html

  <section id="selected_navigator">
    .....
  </section>
  
```

## Banner

1. Hero Banner
2. Hero Slide
   
banner.blade.php
```html

  <section id="selected_headerbanner">
    .....
  </section>

```

## Footer

การทำงานเหมือนเดิม (เปลี่ยน css) โดยมีหลากหลายดีไซต์โดยใส่ตัวแปรมาทั้งหมด

footer.blade.php
```html
  <div class="" data-footer="1">
    .....
  </div>

```

## Code Mobile Menu

เดิมวางไว้ล่างสุด การทำงานคงเดิมโดยพื้นหลังเมนูบาร์ตามดีไซต์แต่ submenu ใส่สีพื้นคงที่เป็นสีเทาดำ ตัวอักษรขาว

```html
  <div id="selected_navigator-mobile">
    {!! $mobileMenu !!}
  </div>
```

