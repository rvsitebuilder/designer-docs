## Menu
การวางตำแหน่งจุดต่างๆ
1. top
2. menu
3. left sidebar
4. right sidebar
5. bottom
   
ถ้าใช้ uikit V3 https://getuikit.com/docs/nav

เช่น
menu.blade.php

```html

  <section id="selected_navigator">
    .....
  </section>
  
```

โค้ด db เหมือนเดิมโดยเริ่มจากแท็ก `<nav>...</nav>` แต่ถ้าอยู่ใน sidebar ต้องเพิ่มคลาสบนแท็ก Sidebar หรือ aside Tag เพื่อใช้ควบคุม (Overwrite) คลาสบางคลาสของเมนู

เช่น
แนวนอน

```html
  <div>
    <nav>
      <ul>
        <li><a><span><i class=”rv-icon”></i> Home</span><div class=”rv-badge”></div></a></li>
        <li><a><span><i class=”rv-icon”></i> About</span><div class=”rv-badge”></div></a></li>
        <li><a><span><i class=”rv-icon”></i> Event</span><div class=”rv-badge”></div></a></li>
      </ul>
    </nav>
  </div>
```

แนวตั้ง 

```html
  <aside class=”nav-vertical”>
    <nav>
      <ul>
        <li><a><span><i class=”rv-icon”></i> Home</span><div class=”rv-badge”></div></a></li>
        <li><a><span><i class=”rv-icon”></i> About</span><div class=”rv-badge”></div></a></li>
        <li><a><span><i class=”rv-icon”></i> Event</span><div class=”rv-badge”></div></a></li>
      </ul>
    </nav>
  </aside>
```