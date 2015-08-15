
# Learn LESS in 10 Minutes (or Less)


We now have CSS pre-processors such as [Less](http://lesscss.org/), [Sass](http://sass-lang.com/) and [Stylus](http://learnboost.github.io/stylus/). They give us a number of benefits over plain CSS:

 * Variables, so that you can define and easily change values throughout your stylesheet. (This is actually coming to CSS some day.)
 * Dynamically calculated values. (In CSS we recently got calc, but it is only for length units.)
 * Mixins, which enable you to reuse and combine styles. They even support passing arguments.
 * Functions, which give you a number of handy utilities for manipulating color, converting images to data-uris and more.
  
The negative aspect is that if you use one of these pre-processors, you will need to compile your stylesheets down to regular CSS so that it works in browsers.

Now, let's start with LESS:

##Getting Started:
If you have node installed, and you know what a terminal is, go ahead and open one. Then install less using NPM:
```
npm install -g less
```
This will give you access to the lessc command from any open terminal, enabling you to compile your .less files into vanilla CSS like this:
```
lessc styles.less > styles.css
```

##Variables:

```
@background-color: #ffffff;
@text-color: #1A237E;
p{
  background-color: @background-color;
  color: @text-color;
  padding: 15px;
}
ul{
  background-color: @background-color;
}
li{
  color: @text-color;
}
```

##Mixins

LESS enables us to use an existing class or ids and apply all it’s styles directly to another selector. The following example will clear things up:
```
#circle{
  background-color: #4CAF50;
  border-radius: 100%;
}
#small-circle{
  width: 50px;
  height: 50px;
  #circle
}
#big-circle{
  width: 100px;
  height: 100px;
  #circle
}
```
or

```
#circle(@size: 25px){
  background-color: #4CAF50;
  border-radius: 100%;
  width: @size;
  height: @size;
}
#small-circle{
  #circle
}
#big-circle{
  #circle(100px)
}
```

##Nesting and Scope

```
@text-color: #000000;
ul{
  @text-color: #fff;
  background-color: #03A9F4;
  padding: 10px;
  list-style: none;
  li{
    color: @text-color;
    border-radius: 3px;
    margin: 10px 0;
  }
}
```

##Operations


You can do basic math operations to numerical values and colors. Lets say we want to have two divs placed next to each other, the second one being twice as wide and with a different background.
```
@div-width: 100px;
@color: #03A9F4;
div{
  height: 50px;
  display: inline-block;
}
#left{
  width: @div-width;
  background-color: @color - 100;
}
#right{
  width: @div-width * 2;
  background-color: @color;
}
```
LESS knows what the measuring units are and won’t mess them up.
```
div {
  height: 50px;
  display: inline-block;
}
#left {
  width: 100px;
  background-color: #004590;
}
#right {
  width: 200px;
  background-color: #03a9f4;
}
```

##Functions
LESS has functions too! It’s starting to look more and more like a programming language, isn’t it?

Let’s take a look at fadeout, a function that decreases the opacity of a color.
```
@var: #004590;
div{
  height: 50px;
  width: 50px;
  background-color: @var;
  &:hover{
    background-color: fadeout(@var, 50%)
  }
}
```

The ampersand (&) is replaced with the parent selector, which results in this CSS:
```
div {
  height: 50px;
  width: 50px;
  background-color: #004590;
}
div:hover {
  background-color: rgba(0, 69, 144, 0.5);
}
```

###Further reading
   
   You now know enough of Less to get started! Every CSS file is a valid Less stylesheet, so you can start cleaning up that old and unwieldy .css right away. As you learn more, you will be able to make the code even better. Here is what we recommend that you read next:
   
   *All the language features – [link](http://lesscss.org/features/#features-overview-feature)
   *LESS function reference – [link](http://lesscss.org/functions/)
   *Editor and compiler in the browser – [link](http://less2css.org/)


