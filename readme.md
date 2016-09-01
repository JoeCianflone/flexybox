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
