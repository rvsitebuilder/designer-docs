## Contenteditable

การใช้ section ใดๆ ที่สามารถแก้ไขได้ ภายใต้ data-editor="block" ต้องระบุ contenteditable="true" และถ้าหากต้องการแสดงข้อมูลใดๆ แต่ไม่ต้องการให้แก้ไขให้เปลี่ยน value เป็น false เพื่อให้สอดคล้องกับเครื่องมือใน Layout Editor 
  
เช่น

```html
  <div class="mg" data-editor="section" data-css="uikit3">

      <div class="uk-grid">
        <div data-editor="block">  
          <div contenteditable="true">
            Edit content here
          </div>
        </div>
      </div>

  </div>
```
