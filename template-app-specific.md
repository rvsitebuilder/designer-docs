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

......... email layout template (ต้องออกแบบใหม่) .......
│   ├── resource/view/admin/emailtemplate/index.blade.php
│   ├── resource/view/admin/emailtemplate/content.blade.php

......... email content template (ต้องออกแบบใหม่) .......
│   ├── resource/view/admin/??????
│   ├── resource/view/admin/??????

......... overwriting other apps ......
│   ├── packages/rvsitebuilder/blog/resources/views/admin/create.blade.php


```

## Template

![DesignerDashboard](images/layout.jpg)

