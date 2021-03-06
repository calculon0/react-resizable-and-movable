# react-resizable-and-movable

Resizable and movable component for React.

[![Build Status](https://travis-ci.org/bokuweb/react-resizable-and-movable.svg?branch=master)](https://travis-ci.org/bokuweb/react-resizable-and-movable)
[![License](http://img.shields.io/npm/l/object.assign.svg)](https://github.com/bokuweb/react-resizable-box#license)

## Demo

![screenshot](https://raw.githubusercontent.com/bokuweb/react-resazable-and-movable/master/screenshot.gif)
See demo: [http://bokuweb.github.io/react-resizable-and-movable](http://bokuweb.github.io/react-resizable-and-movable)

## Important Note

This is an alpha release. Use with caution and hope.

## Installation

```sh
npm i react-resizable-and-movable
```

## Overview

### Basic

``` javascript
      <ResizableAndMovable
         start={{x:20, y:20, width:200, height:200}}
        <p>Example</p>
      </ResizableAndMovable>
```

### With min/max width/height and callbacks

``` javascript
      <ResizableAndMovable
         start={{x:20, y:20, width:200, height:200}}
         minWidth={200}
         minHeight={200}
         maxWidth={300}
         maxHeight={300}
         onResizeStart={() => console.log('resize start')}
         onResize={size => console.log(size)}
         onResizeStop={size => console.log('resize stop')}
         onDragStart={() => console.log('drag start')}
         onDrag={(e, ui) => {
           console.dir(ui);
           console.log(e);
         }}
         onDragStop={(e, ui) => console.log('drag stop')}
         isResizable={{x:true, y:true, xy: true}}>
        <p>Example</p>
        <p>start 200px x 200px</p>
        <p>min 200px x 200px</p>
        <p>max 300px x 300px</p>
      </ResizableAndMovable>
```
## Properties

#### start {x: number, y:number, width:number, height:number}

Specifies the `x` ,`y`, `width` and `height` that the component should start at.


#### minWidth {number}

Specifies the minimum width of the component.
This is generally not necessary to use.

#### minHeight {number}

Specifies the minimum height of the component.
This is generally not necessary to use.

#### maxWidth {number}

Specifies the maximum width of the component.
This is generally not necessary to use.

#### maxHeight {number}

Specifies the maximum height of the component.
This is generally not necessary to use.

#### customClass {string}

The css class set on the component.
This is generally not necessary to use.

#### customStyle {object}

The css style set on the component.
This is generally not necessary to use.

#### isResizable {object}

The permission of x, y, xy direction resizing.   
If omitted, x, y, xy direction resizing is enabled.    
Forexample, If you want to permit only x direction resizing, set `{x:true, y:false, xy:false}`. 
Default value is `{x:true, y:true, xy:true}`.

#### moveAxis {string}

The direction of allowed movement (dragging) allowed ('x','y','both','none').

#### onClick {func}

Callback called on component clicked.

#### onTouchStart {func}

Callback called on component touched.

#### onResizeStart {func}

Callback called on resize start.   

#### onResize {func}

Callback called on resizing.   
Receives the box size `{width: number, height: number}` as argument.

#### onResizeStop {func}

Callback called on resize stop.
Receives the box size `{width: number, height: number}` as argument.

#### onDrageStart {func}

Callback called on dragging start.   

#### onDrage {func}

Callback called on resizing.   
`onDrag` called with the following parameters:



``` javascript
(
 event: Event,
 ui:{
      deltaX: number, deltaY: number,
      node: Node
      position:
      {
        left: number, top: number
      }
   }
)
```

#### onDrageStop {func}

Callback called on dragging stop.
`onDragStop` called with the following parameters:



``` javascript
(
 event: Event,
 ui:{
      deltaX: number, deltaY: number,
      node: Node
      position:
      {
        left: number, top: number
      }
   }
)
```

#### initAsResizing {object}

The component begins as if a resize event occurred. 
This is useful if you would like to click and drag to create a box (e.g. click and drag out a selection window). 
If omitted, component does not call resize when created. 

Accepted Value: `{enable:true, direction: 'both', event:event}` where direction can be 'x', 'y' or 'xy' and event is the current mouse event

Forexample, If you wanted to create a box with a click and a drag on a parent, then in that parents onMouseDown event you would do something like this:
```javascript
    parentClickEvent(event){
    event.persist()
     <ResizableAndMovable
        start={{x:20, y:20, width:200, height:200}} 
        initAsResizing={{enable:true, direction:'both',event:event}}
     />
    }
```
Note that `event.persist()` must be called so the mouse event can be passed to ResizableAndMovable

#### bounds {object|string}

Specifies movement boundaries. Accepted values:
 - `parent` restricts movement within the node's offsetParent
    (nearest node with position relative or absolute), or
 - An object with `left, top, right, and bottom` properties.
   These indicate how far in each direction the draggable
   can be moved.

## Test

``` sh
npm t
```

## License

The MIT License (MIT)

Copyright (c) 2016 @Bokuweb

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
