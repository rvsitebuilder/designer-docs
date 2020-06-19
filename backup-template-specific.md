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

```

## Template

อย่าลืม แท็กต่างๆ ที่อยู่ภายใน `<head>…..</head>`

โครงสร้าง Master ประกอยด้วยตัวแปรและเลเอาท์ครอบนอกสุดมี ID และ Class ที่ใช้ในฝั่ง edit mode และ view mode โดยใช้ Flex css ที่สร้างขึ้นมาเองเป็นหลัก

Master.blade.php

```html
<!DOCTYPE html>
<html lang="{{ app()->getLocale() }}">
  <head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />

    <!-- Start SEO / Title -->
    <title>{!! $title !!}</title>

    <!-- Start Favicon -->
    <link rel="icon" href="/storage/images/favicon.ico" sizes="32x32" />

    <!-- SEO -->          
      {!! optional($seo)->tag !!}
      {!! $embed->siteMeta !!}
      {!! $embed->pageMeta !!}

    <!-- CSRF Token -->
    <meta name="csrf-token" content="{{ csrf_token() }}" />

    <!-- Meta from blade section -->
    @yield('meta')

    <!-- DNS-Prefetch and Preconnect -->        
    <link rel="dns-prefetch" href="{{ config('rvsitebuilder/wysiwyg.wex.cdn.cdnURL') }}"> 
    <link rel="dns-prefetch" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin> 

    <!-- CSS -->        
    @include('user.includes.ukv2')

		<!-- Stack Style -->
		@stack('package-styles')
    <link rel="stylesheet" id="menuCss" type="text/css" href="{{ Storage::url('myheader/menu/'.$bannerStyle->menu_style) }}">
    <link rel="stylesheet" id="headerCss" type="text/css" href="{{ Storage::url('myheader/header/'.$bannerStyle->banner_style) }}">
    <link rel="stylesheet" id="topmenuCss" type="text/css" href="{{ Storage::url('myheader/topmenu/'.$bannerStyle->topmenu_style) }}">
    <link rel="stylesheet" id="footerCss" type="text/css" href="{{ Storage::url('myheader/footer/'.$bannerStyle->footer_style) }}">
    {{ style( @mixstorage('myheader/theme/theme.css') ) }}

    {!! $embed->siteCss !!}
    {!! $embed->pageCss !!}

    <!-- Jquery and global variables -->
    <script src="https://code.jquery.com/jquery-3.4.1.min.js" integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo="crossorigin="anonymous"></script>
		<script>
			window.Laravel =  {"csrfToken":"{{csrf_token()}}"}
  		var viewmode = "{{ $viewmode }}";
  		var editmode = "{{ $editmode }}";
  	 	</script>
		@if ($editmode)
		<script>
        var tagActive = {};
        var ObjectImage = false;
        var lineTable = false;
        var loadScriptExt = {};
        var imageCur = false;
        var editerCur = false;
        var countEffectPreview = 0;
        var breakEvent = false;
        var dynamicLock = false;
        var dynamicShow = false;
        var tableMode = false;
        var startIndex, changeIndex, uiHeight;
        var isForm = false;
        var clickFromEdit = false;
        var oFormUIKIT = false;
        var nviActive = true;
        var frameBody = '';
				var curImage = '';
				var RVwys = {};
				var wys = {};
				var aLang = {};
				var themeName = 'uikit';
      </script>
      @endif
	  @include('rvsitebuilder/core::user.data.mex')	   

  </head>

  @stack('wysiwyg-section')

  <body id="js-applayout">
    <div class="js-bodyTemplate bodyTemplate">

        <!-- เริ่ม Template Website สำหรับไฟล์ Template App Overwrite -->
        <div data-editor="editor" data-css="uikit3">
          <div class="uk-container uk-container-center {{ $fullwidth }}"><!-- Set Website Full width -->  
            <div id="app">
              @include('includes.partials.logged-in-as')
              <header id="selected_header">
                {!! $header !!}
              </header>

              <main>
                <div class="container">
                  <div id="selected_body">
                    <div class="rv-container rv-container-center">
                      <!-- Start Breadcrumbs -->
                      {!! $Breadcrumbs !!}
                      <!-- End Breadcrumbs -->
                    </div>
                    <div class="rv-container rv-container-center">
                      <!-- Start aside1-->
                      {!! $Left Sidebar !!}
                      <!-- End aside1-->

                      {!! $Page !!}

                      <!-- Start aside2-->
                      {!! $Right Sidebar !!}
                      <!-- End aside2-->
                    </div>
                  </div>
                </div>
                <!-- End Container -->
              </main>

              <footer id="selected_footer">
                <div id="rvcmsfooter" class="editable_area">
                  <div class="mg">
                    {!! $footer !!}
                  </div>
                </div>
              </footer>

              <!-- Navigation Mobile Compatible view-->
              <div id="selected_navigator-mobile">
                {!! $MobileMenu !!}
              </div>
              <!-- End Navigation Mobile Compatible view-->

          </div> 
        </div> <!-- End app -->
      </div><!-- End data-theme -->
      
    </div><!-- End bodyTemplate -->
  </body>
</html>
```

@TODO: ย้ายไว้ด้านบน <div class="bodyTemplate"> เนื่องจากใช้ใน editmode อย่างเดียว มีผลให้ fullwidth พัง js เรียกลำดับคลาส selector ย้อนขึ้น ต้องแก้ใหม่โดยใช้ data-editor

@TODO: {!! $title !!} : ให้ใส่เป็น Variable เมื่อโปรแกรมเสร็จแล้วต้องมาแทนค่าใหม่
       js-applayout : เดิมคือ id="app-layout" jsเรียกใช้งาน (/js/plugins/SiteTheme/init.js) 
       app : คือ id="app" jsเรียกใช้งาน (assets/js/app.js) 
       {{ $fullwidth }} ใช้ในการตั้งค่า fullwidth ทั้งเว็บไซต์ ที่เมนู Design >> Website
       data-editor="editor" : ใช้งานกับ Editor WYS
       data-css="uikit3" :  ใช้งานกับ css framework อะไร
       bodyTemplate : js เรียกใช้งานหลายที่กับเลเอาท์ฝั่ง edit mode สำหรับ css ใช้กับเมนูกลุ่ม Responsive Mode 

## Head Tag

แท็กต่างๆ ที่อยู่ภายใน `<head>…..</head>`
Site Config , Favicon, css/js Component, css/js ของ RVsitebuilder, Theme/Custom


## Body

เริ่มแท็ก `<body>…..</body>`
แสดง โครงสร้าง Template ประกอบด้วย `<header>..</header>, <main>..</main>, <footer>..</footer>` มี id #selected_header, #selected_body, #selected_footer, #selected_navigator-mobile อยู่ในแต่ละแท็ก

- โดย ID และ Class ที่ใช้ในฝั่ง edit mode เช่น #app-layout, .bodyTemplate, #app {{ $fullwidth }} ค่า config ที่ใช้ในโปรแกรมเดิม
- ภายใน `<main>..</main>` เรียกไฟล์ blade เลเอาท์ของ sidebar เช่น layout1.blade.php, layout2.blade.php, layout3.blade.php, layout4.blade.php
- ประกอบด้วย {!! $header !!}, {!! $Breadcrumbs !!}, {!! $Sidebar Left !!}, {!! $footer !!},.... จะแทนค่าโดยเรียกมาจากไฟล์ blade

## Header

การทำงาน เรียงสลับกันได้,กำหนด overlap, ซ่อน Banner ได้เหมือนเดิม

โดยการเรียงสลับกันแบ่งเป็น

```html
<section id="selected_topmenu">...</section>
<section id="selected_navigator">...</section>
<section id="selected_headerbanner">...</section>
```

(config เก่า div เก่ายังเอาอยู่) จาก CDN / lib

header.blade.php

```html
<div class="selected_overlap {{ class-design }}">
  <!-- ถ้าเมนู Overlap แบนเนอร์ ใส่คำว่า Overlap -->

  <section id="selected_topmenu">
    <!-- ตัดเป็น top.blade.php -->
    <nav id="topmenu" class="topmenudesign">
      <div class="mg">
        <div class="uk-container uk-container-center rv-block-full">
          <div class="rvsb_design_block bgContent bgTopmenu">
            <div class="uk-container uk-container-center">
              <div class="uk-grid">
                <div class="uk-width-small-1-1">
                  <div class="uk-float-left">
                    <div class="uk-vertical-align-middle uk-hidden-small">
                      <div class="rv_logo"><logo>[[LOGO]]</logo></div>
                    </div>
                  </div>

                  <div class="uk-float-left">
                    <div class="topmenu-minwidth"><tel>[[TEL]]</tel></div>
                  </div>

                  <div class="uk-float-right">
                    <top_nav>[[TOP_NAV]]</top_nav>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </section>

  <section id="selected_navigator">
    <!-- ตัดเป็น navigation.blade.php -->
    <div class="uk-container uk-container-center rv-block-full">
      <div id="rvnavigator">
        <nav
          class="uk-navbar"
          data-uk-sticky="{top:-200, animation: 'uk-animation-slide-top '}"
        >
          <div class="uk-container uk-container-center">
            <div class="uk-float-left">
              <div class="rv_logo uk-navbar-nav uk-hidden-small"></div>
              <span class="js-left-nav">[[LEFT_NAV]]</span>
            </div>
            <div class="uk-float-right">
              <span class="js-right-nav">[[RIGHT_NAV]]</span>
            </div>
          </div>
          <a
            href="#offcanvas"
            class="uk-navbar-toggle uk-visible-small"
            data-uk-offcanvas=""
          ></a>
          <div class="uk-navbar-brand uk-navbar-center uk-visible-small">
            <logo_mobile>[[LOGO_MOBILE]]</logo_mobile>
          </div>
        </nav>
      </div>
    </div>
  </section>

  <section id="selected_headerbanner {{ class-design }}">
    <!-- หากจะซ่อนแบนเนอร์ระบุ uk-hidden -->
    <div id="editable_area_content-s" class="editable_area">
      <div class="mg">
        <div class="rv-container rv-container-center rv-block-full">
          <!-- เริ่มโค้ดสไลด์ -->
          <div
            id="rvs-uk-slide"
            class="uk-slidenav-position"
            data-uk-slideshow=""
          >
            <ul class="uk-slideshow">
              [[BANNER]]
            </ul>
            <!-- case:มี slide มากกว่า1 -->
            [[BANNER_BUTTON]]
          </div>
        </div>
      </div>
    </div>
  </section>
</div>
```

## Top menu

Top menu `<section id="selected_topmenu"> ..</section>`
Topmenu การทำงานเหมือนเดิม แต่ในดีไซต์เปลี่ยน css เป็นแบบใหม่ ตัวแปรยังคงเหมือนคือ [[LOGO]], [[TEL]], [[TOP_NAV]] มีเลเอาท์หลายดีไซต์
เพิ่มเติม: ซ่อนแถบ topmenu ได้

## Navigation

Navigation / Menu Mobile (มี blade แต่ละดีไซต์ )
`<section id="selected_navigator"> ..</section>`
Navigation เหมือนเดิม แต่ถ้าอยู่ใน sidebarต้องเพิ่ม Class บนแท็ก div Sidebar หรือ Aside Tag เพื่อใช้ควบคุม (Overwrite) class บาง class ของเมนู
เช่น

```
แนวนอน

<div>
  <nav>
    <ul>
      <li><a><span><i class=”rv-icon”></i> Home</span><div class=”rv-badge”></div></a></li>
      <li><a><span><i class=”rv-icon”></i> About</span><div class=”rv-badge”></div></a></li>
      <li><a><span><i class=”rv-icon”></i> Event</span><div class=”rv-badge”></div></a></li>
    </ul>
  </nav>
</div>

แนวตั้ง

<aside class=”nav-vertical”>
  <nav>
    <ul>
      <li><a><span><i class=”rv-icon”></i> Home</span><div class=”rv-badge”></div></a></li>
      <li><a><span><i class=”rv-icon”></i> About</span><div class=”rv-badge”></div></a></li>
      <li><a><span><i class=”rv-icon”></i> Event</span><div class=”rv-badge”></div></a></li>
    </ul>
  </nav>
</ aside>
```

Submenu เดิม : บางดีไซต์ เหมือนเดิม ปัจจุบันเก็บ data ทั้งแท็ก ul li a
Submenu ใหม่ : หากมีโค้ดแตกต่างกัน เช่น Mega menu เพิ่ม/เก็บโค้ด data อย่างไร

## Banner

Banner `<section id="selected_headerbanner"> ..</section>`

- ขนาดภาพมีผลกับความสูงของสไลด์
- จะกำหนดขนาดคงที่
- จะอัพโหลดขนาดอะไรก็ได้แล้วให็โปรแกรมจัดการ
- บางรูปอาจจะมีข้อความในนั้น การย่อรูปจะเป็นอย่างไร

1. Hero (bg)

- แบบไม่มีข้อมูล tag content ใดๆบนแบนเนอร์ ในมือถือต้องมี tool setting : background-size: contain; เพื่อย่อตามจอ
- แบบที่มีข้อมูล `<p>..</p>,<div>..</div>` ความสูง Banner จะตาม Content โดยภาพเป็นพื้นหลังขยายขนาดตามอัตโนมัติ(cover)

2. Image ( `<img src=””…>`) ล้วนๆขนาดตามสเกล image จริง
3. Slide (Component แบบไหน uikit3, bootstrap, flexslide, carousel)

- แบบ bg (สำหรับ uikit2 ใส่เป็น `<img src=””…>` แต่จะถูก compile เป็นภาพื้นหลัง)
- แบบ tag image ตรงๆ (สำหรับ uikit3 ใส่เป็น `<img src=””…>` )
- ปล. เป็นระบบ banner slide Manager (เพิ่ม/ลบรูปได้, ปรับตำแหน่ง text block และใส่ effect ได้) ???

## Layout (Left Sidebar / Page Content / Right Sidebar)

- เปลี่ยนคลาส Grid Block จะต้องเปลี่ยน css
- ส่วนคลาสที่ js เรียกใช้ใน Edit Mode ยังคงเดิมคือ (layoutfix, editable_area_content1, editable_area designBlock)

แบ่งเป็นไฟล์ layout1.blade.php, layout2.blade.php, layout3.blade.php, layout4.blade.php

```html
<div class="rv-container rv-container-center rv-block-full">
  <!-- Set Sidebar delete rv-block-full -->
  <!-- Set Row Full width must use class of Design block -->
  <div class="rv-grid">
    <div
      class="aside aside-1 design-block sidebar-left"
      rv-layout="25"
      style="display:none;"
    >
      <div class="layoutfix">
        <aside>
          <section>
            <div id="editable_area_content1" class="editable_area designBlock">
              {!! $Navigation!!}
              <!--sidebar-right.blade.php -->

              {!! $sidebarLeft !!}
              <!-- (lib/Tempalte/Template.php มีโค้ด uikit อยู่) -->

              เรียกไฟล์ section.blade.php อื่นๆที่มากับ template ได้
            </div>
          </section>
        </aside>
      </div>
    </div>

    <!-- Main -->

    <div class="main design-block sidebar-center" rv-layout="100">
      <div class="layoutfix">
        <div id="editable_area_content" class="editable_area designBlock">
          {!! $breadcrumbs!!} @include('includes.partials.messages')
          @if($slug->isSystem() || $slug->isPost() || $slug->isCategory() ||
          $slug->isNonEditble() || \$slug->isPage()) @yield('content') @endif
          เรียกไฟล์ blade Section อื่นๆที่มากับ template ได้
        </div>
      </div>
    </div>

    <div
      class="aside aside-2 design-block sidebar-right"
      rv-layout="25"
      style="display:block;"
    >
      <div class="layoutfix">
        <aside>
          <section>
            <div id="editable_area_content2" class="editable_area designBlock">
              {!! $Navigation!!}
              <!--sidebar-right.blade.php -->

              {!! $sidebarRight !!}
              <!-- (lib/Tempalte/Template.php) -->

              เรียกไฟล์ blade Section อื่นๆที่มากับ template ได้
            </div>
          </section>
        </aside>
      </div>
    </div>
  </div>
</div>
```

โครงสร้าง section และข้อมูล มาจาก lib หรือ template

## Footer

การทำงานเหมือนเดิม (เปลี่ยน css) โดยมีหลากหลายดีไซต์โดยใส่ตัวแปรมาทั้งหมด แต่หากดีไซต์ไม่ต้องแสดงส่วนนั้นๆให้ใส่ uk-footer-displayShow/uk-footer-displayHide

bottom.blade.php

<!-- footer 1  -->

```html
<div class="uk-container uk-container-center rv-block-full" data-footer="1">
  <div class="rvsb_design_block">
    <div id="footerTemplate">
      <div
        class="uk-container uk-container-center rvsb-bg-footer uk-footer-displayShow"
        id="textinfoAndContactFooter"
      >
        <div class="uk-grid">
          <div
            class="uk-width-medium-3-4 uk-margin-bottom uk-footer-displayShow"
            id="textinfoFooter"
          >
            <h3 id="titleInformation">[[TITLEINFO]]</h3>
            <hr id="hrInformation" />
            <div id="contentInformation" style="white-space: pre-wrap;">
              [[CONTENTINFO]]
            </div>
          </div>
          <div
            class="uk-width-medium-1-4 uk-footer-displayShow"
            id="contactFooter"
          >
            <h3 id="titleContact">[[TITLECONTACT]]</h3>
            <ul class="uk-list uk-list-space" id="contactListFooter">
              <li id="liAddressFooter">
                <div class="tableFrame">
                  <div class="tableCell">
                    <span class="uk-icon-justify uk-icon-map-marker"></span>
                  </div>
                  <div class="tableCell">
                    <span id="addressContactFooter">[[ADDRESS]]</span>
                  </div>
                </div>
              </li>
              <li id="liPhoneFooter">
                <div class="tableFrame">
                  <div class="tableCell">
                    <span id="phoneContactFooter"><tel>[[TEL]]</tel></span>
                  </div>
                </div>
              </li>
              <li id="liEmailFooter">
                <div class="tableFrame">
                  <div class="tableCell">
                    <span class="uk-icon-justify uk-icon-envelope-o"></span>
                  </div>
                  <div class="tableCell">
                    <span id="emailContactFooter"
                      ><email>[[EMAIL]]</email></span
                    >
                  </div>
                </div>
              </li>
            </ul>
            <div class="uk-clearfix"></div>
          </div>
        </div>
      </div>

      <div class="uk-container uk-container-center rvsb-bg-footer">
        <div class="uk-grid" id="socailandcopyright">
          <div
            class="uk-width-small-3-4 uk-margin-bottom uk-text-left-small uk-footer-displayShow"
            id="socialbutton"
            onclick="RVwys.widget.ovewEvent(this)"
            panel=".wys-rowFooterSocial"
            widget="rvsitebuilder/core"
          >
            <div class="rv-ribbon"></div>
            <div class="socailFooter uk-text-left-small">
              <img
                class="imgsocial"
                srcs="[[CDN_URL]]/templates/rvs_library/100/images/thumbnails/widget-social.png"
                id="1623f30cde8252f1f2d4460d0c100015"
                width="200"
                height="22"
                border="0"
                data-appname="rvsitebuilder/core"
                widgetname="social"
                setting_socialicon="block"
                setting_social_icon="1"
                setting_label="Follow us"
                setting_facebook_icon="1"
                setting_facebook_link="#"
                setting_twitter_icon="1"
                setting_twitter_link="#"
                setting_google_icon="1"
                setting_google_link="#"
                setting_instagram_icon="1"
                setting_instagram_link="#"
                setting_line_icon="1"
                setting_line_link="#"
                setting_global="1"
                setting_design="1"
                style="display: none;"
              />
            </div>
          </div>
          <div
            class="uk-width-medium-1-4 uk-margin-bottom uk-text-left-small uk-footer-displayShow"
            id="poweredFooter"
          >
            <powered>[[POWERED]]</powered>
          </div>
        </div>
      </div>

      <div class="uk-container uk-container-center rvsb-bg-footer">
        <div class="uk-text-center uk-footer-displayShow" id="sitemapFooter">
          [[SITEMAP]][[LOGIN]]
        </div>
      </div>

      <div class="uk-container uk-container-center rvsb-bg-footer">
        <div class="uk-text-center" id="copyrightFooter">
          <copyright>[[COPYRIGHT]]</copyright>
        </div>
      </div>
      <div class="uk-clearfix"></div>

      <div
        id="getDetailNavigator"
        cmdalign=""
        cmdtextalign=""
        cmdhiddennav=""
        cmdhiddensubmenu=""
      ></div>
      <div id="getContentWidth" cmdWidth=""></div>
    </div>
  </div>
</div>
```

## Code Mobile Menu

เดิมวางไว้ล่างสุด การทำงานคงเดิมโดยพื้นหลังเมนูบาร์ตามดีไซต์แต่ submenu ใส่สีพื้นคงที่เป็นสีเทาดำ ตัวอักษรขาว

```html
<div id="selected_navigator-mobile">
  {!! $MobileMenu !!}
</div>
```

## Section and Block

- Code Section ตัวใหม่จะใช้ css grid ที่สร้างเอง โดยขึ้นต้นด้วย rv ใช้ขีดกลาง เช่น rv-container, rv-container-center
- มีชื่อคลาสที่บังคับใส่เพื่อให้ js เรียกใช้งานได้คงเดิม คือ mg, rv-block-full, rvsb_design_block, bgContent, rv-grid, contenteditable="true"

```html
<div class="mg" data-editor="section" data-theme="uikit3">
  <div class="uk-container uk-container-center uk-block-full lazy">
    <!-- Set Row Full width must use class  of Design block -->
    <div class="rvsb_design_block bgContent">
      <!-- Set Background of Design block -->
      <div class="uk-container uk-container-center">
        <!-- Set Full width must use class  of Design block -->
        <div class="uk-grid-margin"></div>

        <div class="uk-grid">
          <div class="uk-width-medium-1-2" data-editor="block">
            <div contenteditable="true">
              Your Tilte Here
            </div>
            <div class="uk-grid-margin"></div>
          </div>

          <div class="uk-width-medium-1-2">
            <div contenteditable="true">
              Your Tilte Here
            </div>
            <div class="uk-grid-margin"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

@TODO: sssssss
