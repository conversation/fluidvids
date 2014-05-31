# fluidvids.js [![Build Status](https://travis-ci.org/toddmotto/fluidvids.png)](https://travis-ci.org/toddmotto/fluidvids)

Fluidvids is 1KB standalone module that provides a fluid solution for video embeds. By default, fluidvids supports YouTube and Vimeo - but you can easily add your own players. Fluidvids also provides support for dynamically injected (XHR/Ajax/createElement) videos.

Check out a [demo of fluidvids](http://toddmotto.com/labs/fluidvids). Also available as a [WordPress plugin](http://wordpress.org/plugins/fluidvids).

## Methods

#### init()
Pass in your configuration.

```javascript
fluidvids.init({
  selector: ['iframe', 'object'], // runs querySelectorAll()
  players: ['www.youtube.com', 'player.vimeo.com'] // players to support
});
```

#### selector
Type: `Array`

Custom selector(s) that `fluidvids` will search for in the DOM and make fluid.

#### players
Type: `Array` Default: `['www.youtube.com', 'player.vimeo.com']`

Internally constructs a strict `RegExp` which tells `fluidvids` which videos from specific domains to make fluid. This avoids any unwanted videos being parsed and adds developer flexibility.

#### render()
Provides dynamic video support. Using `render()` should only be done when you want to requery the DOM and look for newly added videos, such as `document.createElement('iframe');`. Fluidvids uses internal object caching to lookup `init()` configuration, so it's lightning fast.

```javascript
// run after dynamic elements have been injected
// you'll need to run this each time you need it
fluidvids.render();
```

## Installing with Bower
Use the repository hook:

```
bower install https://github.com/toddmotto/fluidvids.git
```

## Manual installation
Ensure you're using the files from the `dist` directory (contains compiled production-ready code). Ensure you place the script before the closing `</body>` tag.
	
```html
<body>
  <!-- html above -->
  <script src="dist/fluidvids.js"></script>
  <script>
  // fluidvids module available
  </script>
</body>
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using Grunt.

## Release history
- 2.3.0
  - Add support for videos where `height > width`
  - Multiple `selector` support and CSS change to unrestrict element type
  - Add `npm` entry point
  - Change `apply()` to `render()` for better naming
  - Use while loop for and improved loop perf
- 2.2.0
  - XHR/Ajax content support via new `apply()` method to requery DOM
  - Add AMD support
- 2.1.0
  - Fix IE8 bug
- 2.0.0
  - Complete rewrite using Module pattern with public methods
  - Better ability to add custom players
  - Add a custom selector
- 1.2.0
  - Make use of Prototypes
- 1.1.0
  - Better structure
- 1.0.0
  - Initial release
