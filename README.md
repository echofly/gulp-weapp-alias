<div align="center">
  <a href="https://gulpjs.com">
    <img width="200" height="200"
      src="https://upload.wikimedia.org/wikipedia/commons/7/72/Gulp.js_Logo.svg">
  </a>
  <h1>Gulp Weapp Alias</h1>
  <p>Gulp plugin that lets you create custom aliases for wecaht weapp  with an <code>@alias</code> rule. Supports <code>.wxml</code>, <code>.wxss(less|scss)</code>, <code>.js</code> and <code>.wxs</code> file.</p>
</div>

<h2 align="center">Install</h2>

```bash
  npm i gulp-weapp-alias -D
```

<!-- ```bash
  yarn add --dev gulp-weapp-alias
``` -->


<h2 align="center">Usage</h2>

**gulpfile.js**
```js
const { src, dest } = require('gulp');
const aliases = require('gulp-weapp-alias');

function aliasTask() {
    return src('src/*.{wxss|less|scss|wxml|js}')
        .pipe(aliases({
            '@Aliases': "path/to/your/folder",
        }))
        .pipe(dest('dist'));
}
```

the file before compilation

```js
// .js
import * as Utils from '@Aliases/utils/base';
require('@Aliases/utils/base')
```
```less
// .(wxss|less|scss)
@import '@Aliases/style/reset.less';

.bg {
  background-image: url('@Aliases/images/32821027.jpg');
}
```
```html
// .wxml
<import src="@Aliases/wxs/index.wxs" />

<image src="@Aliases/images/32821027.jpg" mode="cover"></image>

```

will become:

```js
// .js
import * as Utils from 'path/to/your/folder/utils/base';
require('path/to/your/folder/utils/base')
```
```less
// .(wxss|less|scss)
@import 'path/to/your/folder/style/reset.less';

.bg {
  background-image: url('path/to/your/folder/images/32821027.jpg');
}
```
```html
// .wxml
<import src="path/to/your/folder/wxs/index.wxs" />

<image src="path/to/your/folder/images/32821027.jpg" mode="cover"></image>

```
