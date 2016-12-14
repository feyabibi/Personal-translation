# ::after

::after is a generated content element that represents a styleable abstract last child of the respective element.

中文译文写在这里

The content inserted using ::after is inserted after other content inside the element and is displayed inline by default. The value of the content is specified using the [content](http://tympanus.net/codrops/css_reference/content) property.

For example, suppose you want to add a small icon to all links that link to pages on websites other than the one the reader is reading. It is usually a good idea to add a small icon that tells the readers that the link they’re about to click will take them to another domain. Such an icon can be added before or after the content of the link. It is common to add it after the content, so that’s what we’re going to do—using ::after we’re going to insert the small icon (external-link) after the content of all links on a page that have a class name .external.

```html
Let's <a href="http://movethewebforward.org/" class="external">Move The Web Forward</a> together!
```

The following snippet will add the icon to the links. The icon will be inserted inline after the content of the link.

```css
.external::after {
    content: url(external-link.png);
    padding-left: 5px; /* create some space between the image and the content before it */
}
```

