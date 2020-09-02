# hoverscroll

### requirements
jQuery 3.5.1+ **(not tested on previous versions)**
jQuery UI 1.12+ (only for custom animation styles, e.g easeInOutQuad etc) **(not tested on previous versions)**

### how to use
first, create a new object

`let hoverScroll = new HoverScroll( (hover-scroll element id or jQuery object), (scroll direction), (list-to-be-scrolled element id or jQuery object) )`

for example, if you want to create two hover scrollers for left and right scrolling, then it should look something like this

`let listElement = $('#list');
let leftHoverScrollElement = $('#left-hover-scroll');
let rightHoverScrollElement = $('#right-hover-scroll');

let leftHoverScroll = new HoverScroll(leftHoverScrollElement, "left", listElement)
let rightHoverScroll = new HoverScroll(rightHoverScrollElement, "right", listElement)`

or this

`let listElement = $('#list');
let leftHoverScrollID = 'left-hover-scroll';
let rightHoverScrollID = 'right-hover-scroll';

let leftHoverScroll = new HoverScroll(leftHoverScrollID, "left", listElement);
let rightHoverScroll = new HoverScroll(rightHoverScrollID, "right", listElement);`

then we can access the following methods

**scrolling a list**
note: once scroll.start() has been called, the list will not stop scrolling until scroll.stop() is called

`scroll.start( (animation style, only if using jQuery UI) )`

this will start the scrolling animation

`scroll.stop()`

this will stop the current scrolling animation

*example*

`$(function() {
	
	leftHoverScrollElement.hover(function() {
		leftHoverScroll.scroll.start();
	}, function() {
		leftHoverScroll.scroll.stop();
	});
	
});`

**check if the scrollers should be visible or not**
this function can show/hide the scroller, depending on the where the user is scrolled to in the list
it should be called by an onscroll event from the chosen list.

*example*
`listElement.scroll(function() {
	leftHoverScroll.check();
	rightHoverScroll.check();
});`

**manually fading in/out the element**
the scroller can be faded in or out manually by using animate.in() or animate.out(). these functions will automatically be called by check()

*example*
`leftHoverScroll.animate.out();
rightHoverScroll.animate.in();`
