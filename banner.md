# Banner
- [Banner](#banner)
- [Hero Banner](#hero-banner)
- [Slide Banner](#slide-banner)

## Banner

จะประกอบไปด้วยข้อมูล static และตำแหน่งของข้อมูลดังกล่าวจะมีหลากหลายดีไซต์ แบ่งเป็น 
1. Hero Banner
2. Slide Banner 

ซึ่งทั้ง 2 แบบจะเขียนโค้ดแตกต่างกัน

## Hero Banner
การทำงานเหมือน section คือ สามารถย้าย Block ได้ ใส่ Effect, Image , Background ได้ ซึ่งการใส่รูปพื้นหล้งนั้นจะขยายรูปให้อัตโนมัติ (Background Cover) ตามจำนวนของข้อมูลที่สัมพันธ์กับความสูงของ Section

```html
<div class="jsheaderimg uk-container uk-container-center rv-block-full lazy">
    ...
</div>
```

## Slide Banner

การทำงานสามารถเปลี่ยนสไลด์, เพิ่ม/ลบ สไลด์ได้ ใส่ Effect Slide ได้

```html
<li data-slideshow-slide="img" data-banner="1" aria-hidden="false">
    ....
</li>
```   
