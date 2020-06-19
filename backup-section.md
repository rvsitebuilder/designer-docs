## Section 
data-editor="section"

```html

<div class="mg" data-editor="section" data-css="uikit2">
  <div class="uk-container uk-container-center uk-block-full lazy">
    <div class="rvsb_design_block bgContent">
      <div class="uk-container uk-container-center">

        <div class="">
          ......
          จำนวน  ฺBlock
          ......
        </div>

      </div>
    </div>
  </div>
</div>
```

@TODO: มีชื่อคลาสที่บังคับใส่เพื่อให้ js เรียกใช้งานได้คงเดิม คือ mg, rv-block-full, rvsb_design_block, bgContent, rv-grid, contenteditable="true"

## Section and Block
```html
<div class="mg" data-editor="section" data-css="uikit2">
  <div class="uk-container uk-container-center uk-block-full lazy">
    <div class="rvsb_design_block bgContent">
      <div class="uk-container uk-container-center">
        <div class="uk-grid-margin"></div>

        <div class="uk-grid">
          <div class="uk-width-medium-1-2" data-editor="block">
            <div contenteditable="true">
              Content
            </div>
          </div>

          <div class="uk-width-medium-1-2" data-editor="block">
            <div contenteditable="true">
              Content
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</div>

```

## Widget Section 

```html

<div class="mg mgwidget" data-editor="section" data-css="uikit3">
    <div class="uk-container uk-container-center rv-block-full lazy">
      <div class="rvsb_design_block bgContent">
        <div class="uk-container uk-container-center">

          <div class="uk-grid uk-grid-small uk-child-width-expand@s uk-text-center">
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
      </div>
    </div>
  </div>

```

## Section Framework

UIKIT3

```html
  <div class="mg" data-editor="section" data-css="uikit3" >
    <div class="uk-container uk-container-center rv-block-full lazy">
      <div class="rvsb_design_block bgContent">
        <div class="uk-container uk-container-center">

          <div class="uk-grid uk-grid-small uk-child-width-expand@s uk-text-center">
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
      </div>
    </div>
  </div>

```
  Bootstrap

```html
  <div class="mg" data-editor="section" data-css="bootstrap" >
    <div class="container rv-block-full lazy">
      <div class="rvsb_design_block bgContent">
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
    </div>
  </div>
```