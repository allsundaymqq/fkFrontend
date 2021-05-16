# What is fkFrontend for ?
> this project aims to ducument every piece of shit about Front-end Dev,cause when you look at others Repo. You May or May not get pissed off for some reason...

## tables of Content
- [HTML/CSS](#HTML-CSS) 
    - -[1、why box-attribute Padding expanded my Box-Container ?](#box-attr)  
    - -[2、why give `<Body>` Tag a background-color, then the full ViewPort filled with that Color?](#static2)  
    - -[3、why do others write Code like bellow ?](#static3)
    - -[4、CSS Position trick,Using position to expand a box ](#static4)
    - -[5、Reasons for inline Element to inline-block](#static5)
    - -[6、The secret of Padding ](#static6)
    - -[7、Img's W and H get stretched with the viewport width only](#static7)
    - -[8、CSS animation BUG](#static8)
    
  
    
- [Liscense](#liscense)

<a name="HTML-CSS"></a>
### HTML/CSS

<a name="box-attr"></a>
#### 1、why box-attribute Padding expanded my Box-Container ?  
e.g.: you set the box-sizing to content-box, but Padding is only squzzing the box-content.   
`{Padding: 20px; width:100px; height: 100px;}`   
    this is a content-box, with fixed W and H ,but You set Paddings, it will squzze the content,content Is Fixed, it will not yield, so then, it will expand padding Width with 20px on its Four side, then you got visible box with 140x140px, but content is still 100x100, the expanded part is Padding.  
    set the box-sizing Attr to `border-box`,because this allows content to be squzzed by Padding, with changable content. So if you set Padding again, it's visible box still 100x100px
    
<a name="static2"></a>
#### 2、why give `<Body>` Tag a background-color, then the full ViewPort filled with that Color?  
solution : because the Attributes in Body, is the state of whole HTML page.   
even if you give the Body height 20px...

<a name="static3"></a>
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

<a name="static4"></a>
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

<a name="static5"></a>
#### 5、Reasons for inline Element to inline-block
first: inline El margin-top/bottom doesn't work, even if it had values  
second: inline El padding doesn't affect the line-height of text  

In Project, we use inline-block to get inline-EL included by its parent block, otherwise padding will somehow expanded out of the parent BOX.  
And, we also wanna inline-El have margin-top/bottom. 
Last, we often use padding to set inline-El W and H...

<a name="static6"></a>
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

<a name="static7"></a>
#### 7、Img's W and H get stretched with the viewport width only
Suppose You wanna make you Web pages scalable...  
like, adjust the ViewPort Width, the Img's W and H can be responsive  
just write css like this:  
```css
//In global.css
    img{
        width:100%;
    }
    
```
If you're using img as Background, then write backgound-size like this:
```css
    .somediv{
        background: url('') no-repeat;
        background-size:100%;
    }
```
<a name="static8"></a>
#### 8、CSS animation BUG
  CASE：You want to make animation effect through 'click' or 'keydown' event, and the callback function is gonna add a new class to a DOM element. Then, you have to add 'transitionend' event to every single Element, using its callback function to remove class of the Element.  
  In short, Using JS to add/remove class from a Element. But it will trigger BUG...  
  ```js
  function addAnimate(e){
    const key = document.querySelector(`.key[data-key="${e.keyCode}"]`);
    key.classList.add('active');
  }
  function removeTransition(e){
    if(e.propertyName !== 'transiform'){ return; }
    this.classList.remove('active');
  }
  const keys = document.querySelectorAll(".key");
  keys.forEach( key => {
    key.addEventListener('transitionend', removeTransition)
  });
  window.addEventListener('keydown', addAnimate);
  ```
  This is typical, but have bugs, like, when you press key very frequent, and the 'acitve' class won't remove, so it's gonna have 'active' class all way long...  
  Solutions: Using @keyFrames and clone 'active' DOM node, then replace current node with the clone one, so that to trigger the Animation process.  
  ```js
  function palySound(e){ 
        const key = document.querySelector(`.key[data-key="${e.keyCode}"]`); 
         
        key.style.animationPlayState = 'running';
        let elm = key;
        let newone = elm.cloneNode(true);
        elm.parentNode.replaceChild(newone, elm); 
        return;
    } 
    window.addEventListener('keydown', palySound); 
  ```
  ```css
  @keyframes highlight {
    0% { 
         
    }
    50% {
        border: .3rem solid orange;
        box-shadow: 0 0 1remorange;
        transform: scale(1.1);
    }
    100% {
        border: .2rem solid #fff;
         
    }
  }
  
.key{  
    animation-name: highlight;
    animation-duration: 0.2s;
    animation-fill-mode: forwards;
    animation-play-state: paused;
 }
  ```

<a name="liscense"></a>
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

