### Template App  

- Master Template File Structure App ใช้ Overwrite
  
## File Structure

```text
.........web template  .......
└── template
│   ├── template.json <--แยกดี หรือ รวมใน app.json ดี
          {css-framework: bootstrap3, master: xxxxx, header: ...., ...}
│   ├── resource/js
│   ├── resource/scss
│                ├── _global.scss
│                ├── _variables.scss
│   ├── resource/images
│   │            └──template-thumb-m.png
│   │            └──template-thumb-l.png
│   │            └──large-preview.png
│   ├── resource/view/user/layouts
│   │                      └── master.blade.php
│   │                      ├── layout1.blade.php
│   │                      ├── layout2.blade.php
│   │                      ├── layout3.blade.php
│   │                      └── layout4.blade.php
│   ├── resource/view/user/menus
│   │                      └── top.blade.php
│   │                      ├── main-left.blade.php
│   │                      ├── main-right.blade.php
│   │                      ├── sidebar-left.blade.php
│   │                      └── sidebar-right.blade.php
│   │                      └── bottom.blade.php
│   ├── resource/view/user/sections
│   │                      └── 1.blade.php  (ใน master ถ้ามี  = overwrite แบบ)
│   │                      └── 2.blade.php  (ใน master ไม่มี = เพิ่มแบบ)
│   ├── resource/view/user/headers
│   │                      └── 1.blade.php
│   │                      └── 2.blade.php
│   ├── resource/view/user/sidebars (section for sidebar)
│   │                      └── 1.blade.php
│   │                      └── 2.blade.php
│   ├── resource/view/user/footers
│   │                      └── 1.blade.php
│   │                      └── 2.blade.php
│   ├── resource/view/user/alert.blade.php


......... overwriting other apps ......
│   ├── packages/rvsitebuilder/blog/resources/views/admin/create.blade.php


```

## Template

![DesignerDashboard](images/layout.jpg)

## Config

template.json ภายในมีอะไรบ้าง (ถ้าโปรแกรมเมอร์ปรับ เพิ่ม ให้มาปรับตรงนี้ด้วย)

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
 - Name : ตั้งชื่อรูปตัวอย่างแท็มเพลต large-preview.png (ซึ่งใช้แสดงตัวอย่างใน step Template)
 - Type of file : .png
 - Image Size : ไม่เกิน 200kb
 - Dimensions : 400 x auto 

 ## Maximum Folder Template
  
- Export / Import โฟล์เดอร์เท็มเพลตรวมกันเป็นไฟล์สกุลใดๆ ไม่เกิน 2 MB ที่ประกอบด้วย Blade File, Thumbnail, Image, template.json, อื่นๆ
- Export / Import โฟล์เดอร์เท็มเพลตเป็นไฟล์สกุล .tar, .tar.gz, .zip
