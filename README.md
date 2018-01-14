# [HTML5 Canvas](https://gk-hynes.github.io/html5-canvas/)

A HTML5 canvas to play with. Built for Wes Bos'
[JavaScript 30](https://javascript30.com/) course.

[![Screenshot of HTML5 CANVAS](https://screenshots.firefoxusercontent.com/images/948ea796-e715-41df-88df-c8294dbe3ed8.png)](https://gk-hynes.github.io/html5-canvas/)

## Notes

### Canvas

You don't draw directly on the canvas element. You draw on the context. The context can be 2D or 3D.

```js
const canvas = document.querySelector("#draw");
const ctx = canvas.getContext("2d");
```

By default the canvas os 800x800px. Set `canvas.width` to be `window.innerWidth` and `canvas.height` to be `window.innerHeight` to make it as big as the window.

When you draw, you need to set a colour and style for the line you are going to create. Set these with `strokeStyle`, `lineJoin` and `lineCap`.

To draw a line you need a starting x and y value and an ending x and y value. Create `lastX` and `lastY` variables to set these.

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

After each stroke update the `lastX` and `lastY` variables. Also, set the `mousedown` event listener so that before someone does a mousemove `lastX` and `lastY` are updated and you don't always start from 0.

### HSL (Hue, Saturation, Lightness)

HSL is an alternative colour system to Hexadecimal or RGBA colours. It takes three values.

`Hue` is a degree on the colour wheel. 0 (or 360) is red, 120 is green, and 240 is blue.

`Saturation` gives a percentage value for the intensity of the colour. 100% is the full colour.

`Lightness` is also measured as a percent. 0% is black, 100% is white, and 50%is the average.

Initially, set the variable `hue` to be 0 .
Set `strokeStyle` to `hsl(${hue}, 100%, 50%)`.
Increment `hue` at the end of the `draw` function.
If `hue` goes over 360 you can reset it to zero.

You can set `lienWidth` to change when `hue` changes.

Alternatively, you can set `direction` to `true` (so `lineWidth` is increasing) and use an if statement to flip the direction if `lineWidth` goes over 100 or under 1.

```js
if (ctx.lineWidth >= 100 || ctx.lineWidth <= 1) {
  direction = !direction;
}
if (direction) {
  ctx.lineWidth++;
} else {
  ctx.lineWidth--;
}
```
