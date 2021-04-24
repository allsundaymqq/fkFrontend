# What is fkFrontend for ?
> this project aims to ducument every piece of shit about Front-end Dev,cause when you look at others Repo. You May or May not get pissed off for some reason...

## tables of Content
- [HTML/CSS](#HTML/CSS)


### HTML/CSS

1、why box-attribute Padding expanded my Box-Container ?
    e.g.: you set the box-sizing to content-box, but Padding is only squzzing the box-content. 
    `{Padding: 20px; width:100px; height: 100px;}`
    this is a content-box, with fixed W and H ,but You set Paddings, it will squzze the content,content Is Fixed, it will not yield, so then, it will expand padding Width with 20px on its Four side, then you got visible box with 140x140px, but content is still 100x100, the expanded part is Padding.
     
    set the box-sizing Attr to `border-box`,because this allows content to be squzzed by Padding, with changable content. So if you set Padding again, it's visible box still 100x100px

2、why give `<Body>` Tag a background-color, then the full ViewPort filled with that Color?
    solution : because the Attributes in Body, is the state of whole HTML page.
    even if you give the Body height 20px...



### MIT License

Copyright (c) 2021 Armand98 `<happiness2020vip@foxmail.com>`

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