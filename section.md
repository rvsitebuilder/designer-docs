## การระบุ Code เพื่อแยก framework

นิยาม
- data-editor="section" คือ โค้ดที่ระบุเพื่อให้ใช้กับเครื่องมือ editor ส่วนของ Section ในโปรแกรมได้
- data-css="uikit3" คือ โค้ดที่ระบุเพื่อแยก framework เช่น uikit3, Bootstrap, Native 
  เช่น `<div class="mg" data-editor="section" data-css="uikit3">...</div>`

- data-editor="block" คือที่ใช้กับเครื่องมือ editor ส่วนของ Block ในโปรแกรมได้ 
  เช่น `<div data-editor="block">...</div>`
  
## Section 

  คือ แท็ก html ที่แบ่งส่วนของข้อมูล โดยส่วนของ Section นั้นต้องระบุ Attribute เพื่อบ่งบอกว่าใช้ framework ใดและสามารถเรียกใช้เครื่องมือ Section Setting ของโปรแกรมได้
  
  เช่น `<div data-editor="section" data-css="framework name" >...</div>`

## Block 

  คือ แท็ก html ที่แบ่งส่วนของข้อมูลในแต่ละ block หรือ Column ที่อยู่ภายใน Section โดยต้องระบุ Attribute เพื่อสามารถเรียกใช้เครื่องมือ Block Setting ของโปรแกรมได้

  เช่น `<div data-editor="block"> ...</div>`


## Example 

UIKIT3

```html
  <div data-editor="section" data-css="uikit3" >

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
@TODO: 
  ให้โปรแกรมเมอร์ใส่ div มีชื่อคลาสที่บังคับใส่เพื่อให้เรียกใช้งานได้คงเดิม คือ mg, rv-block-full, rvsb_design_block, bgContent, rv-grid, contenteditable="true"

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