Flexybox is the flexbox grid builder built on top of the Susy grid system. The awesome thing about Susy is that it does all the math for you...and [math is hard](http://farm9.staticflickr.com/8458/8071526975_7bc933b835.jpg).

## Installing Flexybox

Installing flexybox is simple:

```
bower install flexybox
```

or

```
npm install flexybox-sass --save
```

## Building a grid

First step is defining some settings, well, ok you don't really need to do this since we start you off with some sensible defaults. Let's take a look at our defaults:

```scss
wrap:            wrap,
columns:         12,
direction:       row,
align-items:     flex-start,
align-content:   center,
justify-content: flex-start,
gutter-position: split,
gutters:         0.25,
order:           0,
flex-grow:       0,
flex-shrink:     1,
align-self:      auto
```

These are our defaults, and you're not stuck with them.

So let's start working on our grid. The first thing you need to do is to pull in the sass and initialize the grid.

```scss
@import '../path/to/files/flexybox/flexy'; // pull in the sass

@include flexygrid-settings(); // initialize everything
```

Now remember those default settings? Cool, cool. If you don't like them here's your chance to reset them.  Just pass `flexygrid-settings` a map of the stuff you want to override:

```scss
@include flexygrid-settings((
   wrap:            nowrap,
   align-content:   flex-start
));
```

Sweet, now you've got the grid the way you want so lets start building some stuff.

The first thing you need is to set up your `container`. This doesn't have to be named container, just name it whatever you want.

```scss

.container {
   @include flexygrid();
}
```

Again, this is built off of your default settings, if you'd like to change them you can make those changes here too, I'll show you that a bit later.

Let's get some columns going and we can see what's up from there:

```scss

.main {
   @include flexy-item(8);
}

.sidebar {
   @include flexy-item(4, first);
}
```

So let's break that down up there. The number is pretty simple, that's just the number of columns you'd like to span. In this case our `.main` class will span 8 columns and our `.sidebar` will span 4. By adding the `first` to the sidebar, we're also saying that we'd like that to be `order`ed as the first thing, regardless of actual placement in the HTML.

Simple right?

### What else can it do?

We're not just limited to what you see here, we can build grids and adjust anything setting that you can adjust with flexbox.  So let's dig into some settings.

Flexy uses Sass's `list...` syntax to allow you to naturally tell the grid how you want it to work.

So let's say you want a particular grid to have the content vertically centered, but other grids you don't, so you don't want to set a global setting:

```scss
.container {
   @include flexygrid(middle);
}
```

How about vertical and horizontal centered columns?

```scss
.container {
   @include flexygrid(center, middle);
}
```

Awesome, but what about columns instead of rows?

```scss
.container {
   @include flexygrid(column);
}
```

Let's just mix a bunch-o-stuff together

```scss
.container {
   @include flexygrid(row-reverse, start, middle, content-fill);
}
```

oh but you need one grid item to align bottom?

```scss

.thing1 {
   @include flexy-item(12, bottom);
}
```

Cool, but I need to have this one column pushed all over to the side for some strange reason:

```scss
.thing-smushed {
   @include flexy-item(2);
   @include flexy-push(10);
}
```

##Settings

###Container Settings

####`flex-direction`

**Flexbox Settings**:
`row | row-reverse | column | column-reverse;`

**Flexy Settings:**
`@include flexy-grid(row | row-reverse | column | column-reverse);`

####`flex-wrap`

**Flexbox Settings**:
`nowrap | wrap | wrap-reverse`

**Flexy Settings:**
`@include flexy-grid(no-wrap | wrap | wrap-reverse);`

####`justify-content`

**Flexbox Settings**:
`flex-start | flex-end | center | space-between | space-around;`

**Flexy Settings:**
`@include flexy-grid(start | end | center | space-between | space-around);`

####`align-items`

**Flexbox Settings**:
`flex-start | flex-end | center | baseline | stretch;`

**Flexy Settings:**
`@include flexy-grid(top | bottom | middle | baseline | fill);`

####`align-content`

**Flexbox Settings**:
`flex-start | flex-end | center | space-between | space-around | stretch;`

**Flexy Settings:**
`@include flexy-grid(content-start | content-bottom | content-middle | content-baseline | content-fill);`
