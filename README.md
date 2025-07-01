
* The [p5.js 1.x loadBytes](https://p5js.org/reference/p5/loadBytes/) returns an object with property `data` containing a `UInt8Array` (required because of preload)
* The [p5.js 2.0 loadBytes](https://betap5js.org/reference/p5/loadBytes/) returns the `UInt8Array` directly

All of the above usages in p5.js 1.x remain available with the [preload.js](https://github.com/processing/p5.js-compatibility/blob/main/src/preload.js) compatibility add-on library.

## …using registerPreloadMethod in an add-on libraries

Under to hood, returns a **Promise** from each loadImage, loadSound, and similar functions. Promises are widely used in JavaScript, .js 1.x *(preload)* and p5.js 2.0 *(promises)***, this this line can be removed (the method `loadSound`, in this example, does not need to be registered) and the method can be updated as follows:

```js
function loadSound (path) {
   if(self._incrementPreload && self._decrementPreload){
     // tTis is the check to determine if preload() is being used, as with
     // p5.js 1.x or with the preload compatibility add-on library. The function
     // returns the soundfile.
 
     self._incrementPreload();
 
     let player = new p5.SoundFile(
       path,
       function () {
         // The callback indicates to preload() that the file is done loading
         self._decrementPreload();
       }
     );
     return player;
 
   }else{
     // Otherwise, async/await is being used, so the function returns a ts below, depending on p5.js version

  describe("A white star 
All of the above usages in p5.js 1.x remain available with the [data.js](https://github.com/processing/p5.js-compatibility/blob/main/src/data.js) compatibility add-on library.
