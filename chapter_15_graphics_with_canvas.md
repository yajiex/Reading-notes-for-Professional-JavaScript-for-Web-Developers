# Chapter 15: Graphics with Canvas
* The `<canvas>` element requires at least its `width` and `height` attributes to be set in order to indicate the size of the drawing to be created. Any content appearing between the opening and closing tags is fallback data that is displayed only if the `<canvas>` element isn't supported.
* Images created on a `<canvas>` element can be exported using the `toDataURL()` method. This method accepts a single argument, the MIME type format of the image to produce, and is applicable regardless of the context used to create the image. The `toDataURL()` method throws an error if an image from a different domain is drawn onto a canvas.
* You can erase an area of the canvas by using the `clearRect()` method. This method is used to make an area of the drawing context transparent.
* `isPointInPath()` accepts an x-coordinate and a y-coordinate as arguments. This method can be called anytime before the path is closed to determine if a point exists on the path
* `translate(x, y)` => Moves the origin to the point (x,y). After performing this operation, the coordinates (0,0) are located at the point previously described as (x,y).
* `save` and `restore()`
* The 2D context will automatically draw a shadow along with a shape or path based on the value of several properties:
  1. `shadowColor` => The CSS color in which the shadow should be drawn. The default is black.
  2. `shadowOffsetX` => The x-coordinate offset from the x-coordinate of the shape or path. The default is 0.
  3. `shadowOffsetY` => The y-coordinate offset from the y-coordinate of the shape or path. The default is 0.
  4. `shadowBlur` => The number of pixels to blur. If set to 0, the shadow has no blur. The default is 0.
* `createLinearGradient()` accepts four arguments: the starting x-coordinate, the starting y-coordinate, the ending x-coordinate, and the ending y-coordinate.
* `createRadialGradient()` accepts six arguments corresponding to the center of a circle and its radius. The first three arguments define the starting circle's center (x and y) and radius, while the last three define the same for the ending circle.
* 

