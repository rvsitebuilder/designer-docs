## การระบุ Code เพื่ือแยก framework

- data-editor="section" คือที่ใช้กับเครื่องมือ editor ส่วนของ Section ของโปรแกรมได้
- data-css="uikit3" คือโค้ดที่ระบุเพื่อแยก framework เช่น uikit3, Bootstrap, Native เช่น `<div class="mg" data-editor="section" data-css="uikit3">...</div>`
- data-editor="block" คือที่ใช้กับเครื่องมือ editor ส่วนของ Block ของโปรแกรมได้ เช่น `<div data-editor="block">...</div>`
  
## Section 

UIKIT3

```html
  <div class="mg" data-editor="section" data-css="uikit3" >

      <div class="uk-grid">
        <div data-editor="block">  
          <div contenteditable="true">
            Content
          </div>
        </div>
        <div data-editor="block">  
          <div contenteditable="true">
            Content
          </div>
        </div>
        <div data-editor="block">  
          <div contenteditable="true">
            Content
          </div>
        </div>
      </div>

  </div>

```
@TODO: ให้โปรแกรมเมอร์ใส่ div มีชื่อคลาสที่บังคับใส่เพื่อให้เรียกใช้งานได้คงเดิม คือ mg, rv-block-full, rvsb_design_block, bgContent, rv-grid, contenteditable="true"

  Bootstrap

```html
  <div class="mg" data-editor="section" data-css="bootstrap">

    <div class="container">
      <div class="row">
        <div class="col-md-6" data-editor="block">
          <div contenteditable="true" >
              Content
          </div>
        </div>
        <div class="col-md-6" data-editor="block">
          <div contenteditable="true">
              Content
          </div>
        </div>
      </div>      
    </div>

  </div>
```