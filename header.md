# Header
- [Header](#header)
- [Topbar](#topbar)
- [Menu](#menu)
- [Banner](#banner)

## Header
การทำงาน เรียงสลับกันได้,กำหนด overlap และ ซ่อน Banner ได้เหมือนเดิม โดยโค้ดจะมีโครงสร้างของ topmenu, menu, banner รวมอยู่ เมื่อเข้าใช้งานในโปรแกรมแต่ละส่วนสามารถคลิกเปลี่ยนแบบอื่นๆได้จาก RVsitebuilder > เมนู design

header.blade.php

```html
<div class="selected_overlap {{ class-design }}">
    <section id="selected_topmenu">
    ....
    </section>
       
    <section id="selected_navigator">
    ....
    </section>

    <section id="selected_headerbanner">
    ....
    </section>
</div>
```
@TODO: 
- {{ class-design }} : คือจากแท็มเพลตดีไซต์แบบกำหนดเมนู Overlap กับแบนเนอร์ ต้องใส่คำว่า Overlapด

## Topbar

จะประกอบไปด้วย [[LOGO]], [[TOP_NAV]], [[TEL]], Login/Logout Account และตำแหน่งของข้อมูลดังกล่าวจะมีหลากหลายดีไซต์

```html
<section id="selected_topmenu">
    ....
</section>
```

## Menu

จะประกอบไปด้วย [[LOGO]], [[LEFT_NAV]], [[RIGHT_NAV]]  และตำแหน่งของข้อมูลดังกล่าวจะมีหลากหลายดีไซต์

```html
<section id="selected_navigator">
    ....
</section>
```

## Banner

```html
<section id="selected_headerbanner">
    <div id="editable_area_content-s" class="editable_area">
        <div class="mg">
            <div class="uk-container uk-container-center rv-block-full">
                <div id="rvs-uk-slide" class="uk-slidenav-position" data-uk-slideshow="">
                    <ul class="uk-slideshow">
                        [[BANNER]]
                    </ul>
                        [[BANNER_BUTTON]]
                </div>
            </div>
        </div>
    </div>
</section>
```
