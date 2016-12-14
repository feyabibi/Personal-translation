# ::after
###(已翻译完)
::after is a generated content element that represents a styleable abstract last child of the respective element.

::after是生成内容元素,作为元素内容的一个"无形"的子元素插在其最后.


The content inserted using ::after is inserted after other content inside the element and is displayed inline by default. The value of the content is specified using the [content](http://tympanus.net/codrops/css_reference/content) property.

使用::after在元素内容的最后面插入生成内容。默认地，这个伪元素是行内元素,其值由 [content](http://tympanus.net/codrops/css_reference/content) 的属性来指定.


For example, suppose you want to add a small icon to all links that link to pages on websites other than the one the reader is reading. It is usually a good idea to add a small icon that tells the readers that the link they’re about to click will take them to another domain. Such an icon can be added before or after the content of the link. It is common to add it after the content, so that’s what we’re going to do—using ::after we’re going to insert the small icon(![](http://upload-images.jianshu.io/upload_images/3925492-3fc1c89e4dd48cb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240))after the content of all links on a page that have a class name .external.

例如,你想为所有链接添加一个小图标，用来链接到网站上除正在浏览之外的其他网页。 通常我们会添加一个小图标,去告诉用户点击图标将跳转到其他网页, 这样的图标我们可以添加在链接的内容之前或之后.一般添加在内容之后,所以这就是我们要做的—使用::after 伪元素添加一个小图标在页面上所有类名为.external的链接内容之后.
```html
Let's <a href="http://movethewebforward.org/" class="external">Move The Web Forward</a> together!
```

The following snippet will add the icon to the links. The icon will be inserted inline after the content of the link.

下面这段代码将添加图标到链接里.图标将会插入在链接内容的后面。

```css
.external::after {
    content: url(external-link.png);
    padding-left: 5px; /* create some space between the image and the content before it */
}
```
The image is added using the [content
](http://tympanus.net/codrops/css_reference/content) property. Images inserted using pseudo-elements cannot be resized. They are inserted as is, so you will have to size your image before you use it.

使用content属性添加图像,使用伪元素插入的图像无法调整大小,它们是按原大小插入的，所以你必须在使用之前调整好图像的大小。

The result of the above code is the following:

上述代码运行结果如下：

*此处有demo
[demo地址](http://tympanus.net/codrops-playground/SaraSoueidan/dYfExU3k/embed/result,html,css/)
<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/dYfExU3k/embed/result,html,css/" class="codrops-playground-embed" width="100%" height="300px" frameborder="0" scrolling="no" allowfullscreen="true" style="position: relative;"> </iframe>


Because the content inserted using a pseudo-element is not inserted into the DOM, it would normally not be possible to see and inspect the inserted content using a browser’s dev tools. However, Chrome 32+ and Firebug for Firefox allow you to see the pseudo-element’s position in the DOM, and by selecting it you can view the styles associated with it in the CSS panel. Inspecting the above demo in Chrome’s dev tools shows the following result:

因为使用伪元素插入的内容并没有插入到DOM之中，所以这就意味着我们不能通过浏览器的开发者工具去查看和检查插入的内容。 但是，Chrome 32+和Firebug for Firefox允许你查看伪元素在DOM中的位置，并且通过选中它，可以在CSS面板中查看与其相关联的样式。 以下是在Chrome的开发者工具中检查上述demo时显示的结果：

![](http://upload-images.jianshu.io/upload_images/3925492-f7a6cc6fae2ae071.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

The above demo also shows that the content added with ::after
 is positioned inline with and *after* the rest of the content inside the blockquote.    

上面的demo还显示了用:: after添加的内容会并排显示在blockquote的其余内容之后.

Since ::after content is inserted after other content inside an element, this also means that the pseudo-element will be [stacked](http://tympanus.net/codrops/css_reference/z-index) on top of other elements that come before it in the source tree.

因为:: after内容插入在元素中的其他内容之后，这也意味着伪元素将在其他元素之上被[堆叠](http://tympanus.net/codrops/css_reference/z-index) 在源码树中之前的其他元素的顶部。

A pseudo-element can be used to insert almost any kind of content, including characters (as above), strings of text, and images. For example, the following are all valid ::after declarations with valid content:

伪元素可被用于插入几乎任何类型的内容，包括字符（如上），文本字符串和图像。 例如，以下都是有效的:: after声明和内容：
```css
.element::after { 
       content: url(path/to/image.png); /* an image, for example, an icon */
}

.element::after { 
        content: "(To be continued...)"; /* a string */
}

.element::after { 
        content: "\201C"; /* also counts as a string. Escaping the unicode; renders it as a character */
} 
```
The content of ::after can also be a counter, and it can also be left empty.
Empty pseudo-elements are useful for clearing floats in an element. For example, the micro clearfix hack by Nicolas Gallagher uses ::after and ::before to clear the floats inside float containers. You can read more about clearing floats and how the hack works in the float entry.

:: after的内容也可以是一个计数器，也可以为空。
空伪元素对于清除元素中的浮动很有用。 例如，Nicolas Gallagher的micro clearfix hack清除浮动,就是使用:: after和:: before来清除float容器内的浮动。 你可以阅读更多清除浮动相关内容以及 hack在浮动条目中是如何运作。

The pseudo-element ::after can also be styled just like any other content—it can be floated, positioned, and even animated. (Animating pseudo-elements is not possible in all browsers. See the browser support section below for more information.)

伪元素:: after也可以像其他任何内容一样设置样式—它可以是浮动的，定位的，甚至是动画的。 （不是所有浏览器都支持伪元素动画。有关详细信息，请参阅下面的浏览器支持部分。）

The ability to style pseudo-elements as if they were real elements on the page led to using them mostly for “cosmetic” purposes. Pseudo-elements are heavily used to created geometric shapes in CSS, among many other use cases. A demonstration of that can be seen in the following demo. An eight-point star can be created using an element and its pseudo-element. The first four points are created from the element itself made into a square. Then, the element’s pseudo-element is styled to get the same height and width as its parent, it is positioned absolutely on top of its parent, and then rotated by 45 degrees, forming an eight-point star.

由于伪元素可以设置样式,这使得他们看起来像是页面上真实的元素,于是它常被用于"装扮''。 在许多用例中，伪元素被大量用在CSS中创建几何形状。 这个演示可以在下面的demo中看到。 我们可以使用元素及其伪元素来创建一个八角星,一开始的四个角是通过构成正方形的元素自身创建的,接着,将元素的伪元素的宽高设置为与其父元素相同，并且绝对定位在其父元素的顶部，然后旋转45度，最终形成一个八角星。
```css
/* 
    The element and its pseudo-element are both made translucent using the `opacity` property in order to better visualize how the two are positioned in the demo. 
    By removing the opacity values, you can see a fully opaque eight-point star 
*/
.element {
    width: 250px;
    height: 250px;
    background-color: #009966;
    opacity: .8;
    position: relative;
    margin: 100px auto;
}

.element:after {
    content: "";
    position: absolute;
    display: block;
    width: 250px;
    height: 250px;
    background-color: #009966;
    opacity: .8;
    transform: rotateZ(45deg);
}
```
Since the pseudo-element is used as a cosmetic element only, its content can be left empty.

由于在这里伪元素仅作为"装扮"元素,所以内容可以为空.

*此处有demo
[demo地址](http://tympanus.net/codrops-playground/SaraSoueidan/kFTn9yJk/embed/result,html,css/)
<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/kFTn9yJk/embed/result,html,css/" class="codrops-playground-embed" width="100%" height="480px" frameborder="0" scrolling="no" allowfullscreen="true" style="position: relative;">  </iframe>

This demo can also be created similarly using the [::before
](http://tympanus.net/codrops/css_reference/before) pseudo-element.

这个demo也可以使用[:: before
](http://tympanus.net/codrops/css_reference/before)伪元素来创建。

#Trivia & Notes
---
###Different notations: (:) and (::)
###符号:(:)和(::)的区别

You will most likely come across (or have come across) the notation :after
 which uses one colon instead of two.

你很可能会遇到（或遇到了） :after 前面用一个冒号代替两个冒号的情况.


In CSS1 and CSS2, pseudo-elements were defined to start with one colon (:), just like pseudo-classes (for example [:hover
](http://tympanus.net/codrops/css_reference/hover)). In CSS3, the double colon notation (::) was introduced for pseudo-elements in order to differentiate them from pseudo-classes.

在CSS1和CSS2中，伪元素被定义为以一个冒号（:)开头，就像伪类一样（例如[：hover
](http://tympanus.net/codrops/css_reference/hover))。 在CSS3中，双冒号表示法（：:)是为伪元素引入的，以便将其与伪类区分开来。
```css
/* old CSS2 syntax */
.element:after {
    /* content and styles here */
}

/* new CSS3 syntax */
.element::after {
    /* content and styles here */
}
      
```
All browsers that support the two-colon notation also support the one-colon notation. Internet Explorer 8, however, does not support the two-colon notation. So, unless you need to support Internet Explorer 8, you can use the two-colon notation without having to worry about browser support.

所有支持双冒号表示法的浏览器也支持单冒号表示法。 但是，Internet Explorer 8不支持双冒号。 因此，除非你需要支持Internet Explorer 8，不然就可以大胆地使用双冒号表示法，而无需担心浏览器支持。

In all the demos in this entry, the one-colon syntax is used to provide wider browser support for readers viewing the demos in IE8.

在本文档的所有demo中，使用单冒号语法是为给在IE8下浏览demo的读者提供更广泛的浏览器支持。
##Accessibility
##辅助功能
Content added using pseudo-elements is not inserted into the DOM—it is only visually displayed. Hence, screen readers won’t be able to access and read the content generated using pseudo-elements. So, it is recommended that you don’t use pseudo-elements to insert vital content into a page (such as footer notes that are relevant to the article, for example).

使用伪元素添加的内容不会插入到DOM中—只能在视觉上显示。 因此，屏幕阅读器将不能访问和读取使用伪元素生成的内容,所以，建议你不要使用伪元素将重要内容插入页面（例如与文章相关的页脚注释）。

Pseudo-elements are mostly used to insert and style cosmetic content, and should not be relied on to insert content that is relevant to the meaning and completeness of the content on the page.

伪元素主要用于插入和"修饰"内容，并且不依赖于页面上与之相关含义和完整性的插入内容。


Also, since the content inserted using pseudo-elements is not inserted into the DOM, this means that you cannot attach any event handlers to it using JavaScript.

此外，由于使用伪元素插入的内容没有插入到DOM中，这意味着你不能使用JavaScript给它身上绑定任何事件。
#Examples
#例子
---
Pseudo-elements, including ::after, can be used to do a lot of things and create a lot of effects. In addition to the examples above, the following articles contain some examples and use cases for pseudo-elements that we recommend you have a closer look at.

伪元素，包括:: after，可以用来做很多事情和创建很多效果, 除了上面的例子所演示的,下面的文章还包含一些伪元素的用例，我们建议你可以详细阅读。

* [CSS Image Replacement with Pseudo-Elements](http://nicolasgallagher.com/css-image-replacement-with-pseudo-elements/)
* [Using CSS Pseudo Elements :before And :after](https://www.bennadel.com/blog/2445-using-css-pseudo-elements-before-and-after.htm)

##Using ::after to style links for print style sheets
##使用:: after为打印样式表设置样式链接

One very useful use case for the ::after pseudo-element is in print style sheets. Because links cannot be clicked on paper (of course), you should usually include the URL that a link points to right after the link, so that print readers can visit it when they want. The following example does just that:

在打印样式表中::after伪元素有一个非常有用的用例.因为在页面上不能点击链接（这是毫无疑问的），你通常会紧跟着链接后面包一个指向链接的URL，以便打印的读者可以在他们需要时访问它。 下面的例子就是这样：
```css
@media print {
    a[href]::after {
        content: " (" attr(href) ")";
    }
}
```

The above snippet contains multiple CSS concepts: an [attribute selector](http://tympanus.net/codrops/css_reference/attribute-selector) (a[href]), the [content
](http://tympanus.net/codrops/css_reference/content) property, and the attr() function.

上面的这段代码包含多个CSS概念：[属性选择器](http://tympanus.net/codrops/css_reference/attribute-selector) (a [href]),[content
](http://tympanus.net/codrops/css_reference/content)属性和attr()函数.

+ The attribute selector will select all links on a page that have an href attribute.

+ 属性选择器会选择页面上所有具有href属性的链接。

+ ::after tells the browser to select these links and insert the value of the content property after the content of the links.

+ :: after告诉浏览器选择这些链接，并在链接内容之后插入content属性的值。

+ The content property itself accepts many values. One of the values accepted is a string. A string can be split into several parts, each part should be wrapped in quotation marks. Multiple strings will be concatenated into one string. See the content property entry for more details.

+ content属性本身接受许多值. 其中一个是字符串.一个字符串可以分成几个部分,每个部分应该用引号括起来,多个字符串可以拼接成一个字符串,有关详细信息，请参阅内容属性文档。

+ The attr(X) function. A function attr(X) “returns as a string the value of attribute X for the subject of the selector”, that is, for the ::after pseudo-element in this case.

+ attr（X）函数. 函数attr（X）“会将选择器主体的属性X的值作为字符串返回，这种情况下选择器主体是指:: after伪元素。

So the above rule selects all links that have an href attribute (using the attribute selector), retrieves the value of the href attribute using the attr() function, and then uses that value as the content of the ::after pseudo-element, which will be inserted into the links after the link’s content.

因此，上述规则选择所有具有href属性的链接（使用属性选择器），使用attr（）函数检索href属性的值，然后使用该值作为:: after伪元素的内容， 其将被插入到所链接的链接内容之后。

In addition to that, the snippet also uses the media at-rule @media, which is used to specify a set of styles for a certain kind of media (print in this case).

除此之外，上面的代码还使用了@media查询规则,为某种媒体指定一组样式.(在此例子中打印)

The following is a live demo showing this concept in action on a web page.
To restrict this to print style sheets only, you would have to use the media at-rule mentioned above. For the sake of demonstration, we’re applying it to the web page in the example here.

以下是将此概念运用在网页上的在线demo,要将此限制为仅打印样式表，你不得不使用到上文提到的媒体查询规则. 为了示范,我们将在网页中应用这个例子.

*此处有demo
[demo地址](http://tympanus.net/codrops-playground/SaraSoueidan/AuXAZ3c8/embed/result,html,css/)
<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/AuXAZ3c8/embed/result,html,css/" class="codrops-playground-embed" width="100%" height="300px" frameborder="0" scrolling="no" allowfullscreen="true" style="position: relative;"> </iframe>

#Live Demo
#在线演示
---
The following demo uses ::after to add an arrow sign to menu items that open a sub-menu when hovered. The arrow is added inside the content property by escaping its unicode value. This is how glyphs are usually represented and added via CSS.

在下面的演示中使用::after添加一个箭头标志到菜单中，当鼠标悬停在箭头上时会打开一个子菜单.通过转义箭头标志的unicode码,可以将箭头添加在content属性中, 这是通过CSS表示和添加字形的常用方式。

*此处有demo
[demo地址](http://tympanus.net/codrops-playground/SaraSoueidan/RETvk1HZ/embed/result,html,css/)
<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/RETvk1HZ/embed/result,html,css/" class="codrops-playground-embed" width="100%" height="300px" frameborder="0" scrolling="no" allowfullscreen="true" style="position: relative;"></iframe>

When the item is hovered, the arrow pointing down is replaced by an arrow pointing up by changing the value of the string in the [content
](http://tympanus.net/codrops/css_reference/content) property. This is possible because pseudo-elements and pseudo-classes are chainable, so something like: li:hover::after is possible and selects the pseudo-element ::after added to the list item when it is hovered.

当鼠标移入箭头时,我们可以通过改变[content](http://tympanus.net/codrops/css_reference/content)属性值,将箭头指向朝下变为箭头指向朝上,因为伪元素和伪类都是可链接的，所以像：li:hover::after就是在鼠标悬停的时将伪元素:: after 添加在列表项中.
#Browser Support
#浏览器支持
---
The one-colon notation :after is supported in Chrome, Firefox, Safari, Opera, Internet Explorer 8+, and on Android and iOS.

单冒号:after在Chrome，Firefox，Safari，Opera，Internet Explorer 8+以及Android和iOS上支持。

The two-colon ::after syntax is supported in all those browsers, but in Internet Explorer it is supported from version 9 up.

这些所有浏览器都支持双冒号 ::after语法，但在Internet Explorer中，从IE9开始支持。

Animating pseudo-elements is supported in Chrome 26+, Firefox 4+, Safari 6.1+, Opera (post Blink) and Internet Explorer 10+.

在Chrome 26+，Firefox 4+，Safari 6.1+，Opera（post Blink）和Internet Explorer 10+中支持动画伪元素。

#Notes
#小记
Internet Explorer does not support using [z-index
](http://tympanus.net/codrops/css_reference/z-index) on pseudo-elements.

Internet Explorer不支持在伪元素上使用[z-index
](http://tympanus.net/codrops/css_reference/z-index).
#Further Reading
#深入阅读
---
+ [CSS Generated Content, Automatic Numbering, and Lists](https://www.w3.org/TR/CSS2/generate.html#before-after-content)
+ [CSS Selectors Level 3](https://drafts.csswg.org/selectors-3/#gen-content)
+ [Learning To Use The :before And :after Pseudo-Elements In CSS](https://www.smashingmagazine.com/2011/07/learning-to-use-the-before-and-after-pseudo-elements-in-css/)

#Related Entries
#相关文档
---
+ [content](http://tympanus.net/codrops/css_reference/content/)
+ [::selection](http://tympanus.net/codrops/css_reference/selection/)
+ [::before](http://tympanus.net/codrops/css_reference/before/)
+ [::placeholder](http://tympanus.net/codrops/css_reference/placeholder/)
+ [::first-letter](http://tympanus.net/codrops/css_reference/first-letter/)
+ [attr()](http://tympanus.net/codrops/css_reference/attr/)
+ [::first-line](http://tympanus.net/codrops/css_reference/first-line/)
