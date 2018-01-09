# HTML5 Canvas

A HTML5 canvas to play with. Built for Wes Bos'
[JavaScript 30](https://javascript30.com/) course.

[![Screenshot of HTML5 CANVAS](https://screenshots.firefoxusercontent.com/images/948ea796-e715-41df-88df-c8294dbe3ed8.png)](https://gk-hynes.github.io/html5-canvas/)

## Notes

You don't draw directly on the canvas element. You draw on the context. The context can be 2D or 3D.

```js
const canvas = document.querySelector("#draw");
const ctx = canvas.getContext("2d");
```

By default the canvas os 800x800px. Set `canvas.width` to be `window.innerWidth` and `canvas.height`to be `window.innerHeight` to make it as big as the window.

When you draw, you need to set a colour and style for the line you are going to create. Set these with `strokeStyle`, `lineJoin` and `lineCap`.

To draw a line you need a starting x and y and an ending x and y. Create `lastX` and `lastY` variables to set these.

Listen for mousemove and log that event to the `draw` function, which is then called whenever you move your mouse on top of the canvas.

Listen for mousedown, mouseup, and mouseout, and, using functions, set `isDrawing` to either true or false. This establishes click and drag functionality.

To draw, start a path with `beginPath()`, start from an x and y, move the line to another x and y, and call `stroke()`.

```js
ctx.beginPath();
// start from
ctx.moveTo(lastX, lastY);
// go to
ctx.lineTo(e.offsetX, e.offsetY);
ctx.stroke();
```

After each stroke update the `lastX` and `lastY` variables. Also, set the `mousedown` event listener so that before someone does a mousemove update `lastX` and `lastY`so you don't always start from 0.
