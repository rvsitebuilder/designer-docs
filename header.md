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