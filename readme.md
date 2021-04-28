# What is fkFrontend for ?
> this project aims to ducument every piece of shit about Front-end Dev,cause when you look at others Repo. You May or May not get pissed off for some reason...

## tables of Content
- [HTML/CSS](#HTML/CSS)


### HTML/CSS

#### 1、why box-attribute Padding expanded my Box-Container ?  
e.g.: you set the box-sizing to content-box, but Padding is only squzzing the box-content.   
`{Padding: 20px; width:100px; height: 100px;}`   
    this is a content-box, with fixed W and H ,but You set Paddings, it will squzze the content,content Is Fixed, it will not yield, so then, it will expand padding Width with 20px on its Four side, then you got visible box with 140x140px, but content is still 100x100, the expanded part is Padding.  
    set the box-sizing Attr to `border-box`,because this allows content to be squzzed by Padding, with changable content. So if you set Padding again, it's visible box still 100x100px
    

#### 2、why give `<Body>` Tag a background-color, then the full ViewPort filled with that Color?  
solution : because the Attributes in Body, is the state of whole HTML page.   
even if you give the Body height 20px...

#### 3、why do others write Code like bellow ?
```css
*,
*::before,
*::after{
    padding:0;
    margin:0;
    box-sizing: border-box;
}
```
explained:  
3 selectors are related to All html tags, All html tags content::before, All html tags content::after,  
purpose for doing that: margin 0 padding 0, set Boxes are Standarded; box-sizing, set Boxes not expanded by paddings.

#### 4、CSS Position trick,Using position to expand a box  
  sometimes, you have to position a div like this:  
  ```css
<div class="particles">
    <canvas></canvas>
</div>
  ```
  so, the canvas W and H is 100% of the parent div,You wanna .particles to reasonably expand,not to exceed the Nearest Parent with Position value.  
  just write CSS like this :
  ```css
  .particles{
    position:absolute;
    top:0;
    left:0;
    right:0;
    bottom:0;
    overflow:hidden;
    z-index:10;
  }
  ```
  set T/L/R/B to 0, it will expand 100% W and H related to Parent position element.

#### 5、Reasons for inline Element to inline-block
first: inline El margin-top/bottom doesn't work, even if it had values  
second: inline El padding doesn't affect the line-height of text  

In Project, we use inline-block to get inline-EL included by its parent block, otherwise padding will somehow expanded out of the parent BOX.  
And, we also wanna inline-El have margin-top/bottom. 
Last, we often use padding to set inline-El W and H...

#### 6、The secret of Padding
In any given project, we don't write height value to any sigle DIV or Tags.  
Instead, we Using Paddings to set Height of any box...  
!!!Don't set Height value to any boxes...  
```css
    .footer{
        padding: 1em;
        //em is related to parent El's font-size...
    }
```

### MIT License

Copyright (c) 2021 Armand98  &lt;happiness2020vip@foxmail.com&gt; 

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
