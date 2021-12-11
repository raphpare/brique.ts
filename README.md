# Brique.js
Creating cascading layout grids like [Pinterest](https://www.pinterest.com/).

## Install
```
npm i brique --save
```

### Initialize

#### TypeScript
``` ts
import { Brique } from './node_modules/brique/lib/index.js';

const refGrid = document.querySelector('.grid');
new Brique(refGrid);
```

#### JavaScript ES6
HTML file
``` html
<script type="module" src="scripts/main.js"></script>
```
JavaScript file (`scripts/main.js`)
``` js
import { Brique } from './node_modules/brique/lib/index.esm.js';

const refGrid = document.querySelector('.grid');
new Brique(refGrid);
```

## `BriqueOptions` object properties
| Propriété | Type | Required | Description |
| --- | --- | --- | --- |
| columns | number |  true |  Number of columns |
| columnGap | string | false | Spacing between columns |
| rowGap | string | false | Spacing between row |



## Exemples
### EX01: HTML markup example
``` html
<div class="grid">
    <div>
        <h2>Box 1</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
    </div>
    <div>
        <h2>Box 2</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut laboret.</p>
    </div>
    <div>
        <h2>Box 3</h2>
    </div>
    <div>
        <h2>Box 4</h2>
        <p>Lorem ipsum dolor sit amet.</p>
    </div>
    <div>
        <h2>Box 5</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor.</p>
    </div>
</div>
```

### EX02: Default TypeScript implementation
``` ts
import { Brique } from './node_modules/brique/lib/index.js';

const refGrid = document.querySelector('.grid');
new Brique(refGrid);
```

### EX03: Implementation with `BriqueOptions`
``` ts
const refGrid = document.querySelector('.grid');
const options = {
    columns: 4,
    rowGap: '24px',
    columnGap: '16px',
};

new Brique(refGrid, options);
```

### EX04: Watch resize
``` ts
const refGrid = document.querySelector('.grid');
const briqueGrid = new Brique(refGrid);

briqueGrid.watchResize();
```

#### Stop watch resize
``` ts
briqueGrid.stopWatchResize();
```

### EX05: Change options with media queries
``` ts
const refGrid = document.querySelector('.grid');
const briqueGrid = new Brique(refGrid);
const mediaQueryMobile = window.matchMedia('(max-width: 767px)');

function setOptionsBrique() {
    briqueGrid.setOptions({
        ...briqueGrid.getOptions(),
        columns: mediaQueryMobile.matches ? 2 : 3
    });
}

setOptionsBrique();
briqueGrid.watchResize();
mediaQueryMobile.addEventListener('change', setOptionsBrique);
```

### Update rendering on demand
``` ts
briqueGrid.update();
```