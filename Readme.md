#ACE-FORK

- For the original Ace Editor go to https://github.com/ajaxorg/ace
- This is a fork for a personal project


Embedding Ace
-------------

Ace can be easily embedded into any existing web page. You can either use one of pre-packaged versions of [ace](https://github.com/ajaxorg/ace-builds/) (just copy one of `src*` subdirectories somewhere into your project), or use requireJS to load contents of [lib/ace](https://github.com/ajaxorg/ace/tree/master/lib/ace) as `ace`


The easiest version is simply:

```html
<div id="editor">some text</div>
<script src="src/ace.js" type="text/javascript" charset="utf-8"></script>
<script>
    var editor = ace.edit("editor");
</script>
```

With "editor" being the id of the DOM element, which should be converted to an editor. Note that this element must be explicitly sized and positioned `absolute` or `relative` for Ace to work. e.g.

```css
#editor {
    position: absolute;
    width: 500px;
    height: 400px;
}
```

To change the theme simply include the Theme's JavaScript file

```html
<script src="src/theme-twilight.js" type="text/javascript" charset="utf-8"></script>
```

and configure the editor to use the theme:

```javascript
editor.setTheme("ace/theme/twilight");
```

By default the editor only supports plain text mode; many other languages are available as separate modules. After including the mode's JavaScript file:

```html
<script src="src/mode-javascript.js" type="text/javascript" charset="utf-8"></script>
```

The mode can then be used like this:

```javascript
var JavaScriptMode = ace.require("ace/mode/javascript").Mode;
editor.session.setMode(new JavaScriptMode());
```

to destroy editor use

```javascript
editor.destroy();
editor.container.remove();
```


Documentation
-------------

Additional usage information, including events to listen to and extending syntax highlighters, can be found [on the main Ace website](http://ace.c9.io).

You can also find API documentation at [http://ace.c9.io/#nav=api](http://ace.c9.io/#nav=api).

Also check out the sample code for the kitchen sink [demo app](https://github.com/ajaxorg/ace/blob/master/demo/kitchen-sink/demo.js).

If you still need help, feel free to drop a mail on the [ace mailing list](http://groups.google.com/group/ace-discuss), or at `irc.freenode.net#ace`.

Running Ace
-----------

After the checkout Ace works out of the box. No build step is required. To try it out, simply start the bundled mini HTTP server using Node.JS

```bash
node ./static.js
```

The editor can then be opened at http://localhost:8888/kitchen-sink.html. 

To open the editor with a file:/// URL see [the wiki](https://github.com/ajaxorg/ace/wiki/Running-Ace-from-file).

Building Ace
-----------

You do not generally need to build ACE. The [ace-builds repository](https://github.com/ajaxorg/ace-builds/) endeavours to maintain the latest build, and you can just copy one of _src*_ subdirectories somewhere into your project.

However, all you need is Node.js and npm installed to package ACE. Just run `npm install` in the ace folder to install dependencies:

```bash
npm install
node ./Makefile.dryice.js
```

To package Ace, we use the dryice build tool developed by the Mozilla Skywriter team. Call `node Makefile.dryice.js` on the command-line to start the packing. This build script accepts the following options

```bash
-m                 minify build files with uglify-js          
-nc                namespace require and define calls with "ace"
-bm                builds the bookmarklet version
--target ./path    specify relative path for output folder (default value is "./build")
```

To generate all the files in the ace-builds repository, run `node Makefile.dryice.js full --target ../ace-builds`

Running the Unit Tests
----------------------

The Ace unit tests can run on node.js. Assuming you have already done `npm install`, just call:

```bash
npm run test
```

You can also run the tests in your browser by serving:

    http://localhost:8888/lib/ace/test/tests.html

This makes debugging failing tests way more easier.

Contributing
-----------------------------

Ace is a community project and wouldn't be what it is without contributions! We actively encourage and support contributions. The Ace source code is released under the BSD License. This license is very simple, and is friendly to all kinds of projects, whether open source or not. Take charge of your editor and add your favorite language highlighting and keybindings!

Feel free to fork and improve/enhance Ace any way you want. If you feel that the editor or the Ace community will benefit from your changes, please open a pull request. For more information on our contributing guidelines, see [CONTRIBUTING.md](https://github.com/ajaxorg/ace/blob/master/CONTRIBUTING.md).

