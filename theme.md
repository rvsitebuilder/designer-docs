
## Theme

กรณีที่มี Theme Css มากับเท็มเพลต 

## Use variables

กำหนดตัวแปร Value ในไฟล์ variables.scss ซึ่งเราจะกำหนดให้สัมพันธ์กับเครื่องมือในโปรแกรม

```html

    $primary-color: #4dabff;
    $secondary-color: #cccccc;

    $global-text-size: 14px;

    $global-heading-color: #4dabff;
    $global-text-color: #333333;
    $global-link-color: #ffb36b;
    $global-hover-color: #f1ca66;


    h1, h2, h3 {
      color:$global-heading-color;
      font-family:$global-font-heading;
    } 
    body {
      color:$global-text-color;
      font-size: $global-text-size;
      font-family:$global-font-family;
    }
    a, a:hover {
      color:$global-link-color;
      font-size: $global-text-size
      font-family:$global-font-family;
    }
    a:hover  {
      color:$global-hover-color;
    }

```