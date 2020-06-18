## Layout (Left Sidebar / Page Content / Right Sidebar)

เป็นโครงสร้างหน้าเว็บไซต์ประกอบด้วยเลเอาท์แบบต่างๆ ใช้ uikit3 
แบ่งเป็นไฟล์ layout1.blade.php, layout2.blade.php, layout3.blade.php, layout4.blade.php


## Layout Full Page (No Sidebar)

Full Page (No Sidebar)

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

          {!! $userprofile !!} 

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
- ต้องแก้เป็น uikit3
- designBlock: js เรียกใช้หลายที่ ส่วนใหญ่ใช้ใน edit mode
- layoutfix: js เรียกใช้หลายที่ ส่วนใหญ่ใช้ใน edit mode
- เดิม id="editable_area_content" ใช้ทั้ง js และดีไซต์ใน edit mode
- {!! $menuSidebarLeft!!} เรียกจาก menu/sidebar-left.blade.php
- {!! $menuSidebarRight!!} เรียกจาก menu/sidebar-right.blade.php
- {!! $breadcrumbs!!}   เรียกจาก user/partials/breadcrumbs.blade.php
- {!! $userprofile !!} เรียกจาก user/partials/userprofile.blade.php
- {!! $sidebarLeftTemplate !!} เรียกจาก (lib/Tempalte/Template.php)
- {!! $sidebarRightTemplate !!} เรียกจาก (lib/Tempalte/Template.php)
- {!! $contentSection!!}  เรียกจาก (protected/sections/1.blade.php)
- {!! $sidebarSection !!} เรียกจาก (protected/sidebars/1.blade.php)

## Layout (Left Sidebar)

Layout2.blade.php
```html
  xxxxxx
```

## Layout (Right Sidebar)

Layout3.blade.php
```html
  xxxxxx
```

## Layout (Left & Right Sidebars)

Layout4.blade.php
```html
  xxxxxx
```