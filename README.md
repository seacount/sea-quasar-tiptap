# sea-quasar-tiptap

Fork from [quasar-tiptap](https://github.com/donotebase/quasar-tiptap), for upgrade dependencies ([Quasar](https://github.com/quasarframework) => 2.0+ ...).

[![](https://img.shields.io/npm/v/quasar-tiptap-branch.svg?label=version)](https://www.npmjs.com/package/quasar-tiptap-branch)
[![](https://img.shields.io/npm/l/quasar-tiptap-branch.svg)](https://www.npmjs.com/package/quasar-tiptap-branch)

Dependencies

[![](https://img.shields.io/npm/dependency-version/quasar-tiptap-branch/quasar)](https://www.npmjs.com/package/quasar-tiptap-branch)
[![](https://img.shields.io/npm/dependency-version/quasar-tiptap-branch/dev/%40quasar%2Fapp)](https://www.npmjs.com/package/quasar-tiptap-branch)
[![](https://img.shields.io/npm/dependency-version/quasar-tiptap-branch/%40quasar%2Fextras)](https://www.npmjs.com/package/quasar-tiptap-branch)


[![](https://img.shields.io/npm/dependency-version/quasar-tiptap-branch/tiptap)](https://www.npmjs.com/package/quasar-tiptap-branch)

## Installation

###Dependencies

quasar-tiptap is built on top of Quasar Framework and tiptap, therefore it should be used in Quasar App and depends on several packages.

### Install to your project

`npm build`

`npm pack`

`npm install [tgz path]/quasar-tiptap-branch.tgz --save`

or

`npm install sea-quasar-tiptap --save`

### run locally

`npm install`

`quasar dev`

### quasar.conf.js

Use `mdi-v5` icon set and `v-close-popup` directive.
```bash
extras: [
  'mdi-v5'
],
framework: [
  directives: [
    'ClosePopup'
  ]
]
```

### Install plugin

create javascript file `src/boot/tiptap.js`

```vue
import Vue from 'vue'
import { QuasarTiptapPlugin } from 'sea-quasar-tiptap'
import { DEFAULT_LOCALE } from 'sea-quasar-tiptap/src/i18n'

Vue.use(QuasarTiptapPlugin, {
  language: DEFAULT_LOCALE,
  spellcheck: true
})
```

### Import component
```vue
<template>
  <div>
    <quasar-tiptap v-bind="options" @update="onUpdate" />
  </div>
</template>

<script>
import { QuasarTiptap, RecommendedExtensions } from 'quasar-tiptap-branch'
import { Placeholder } from 'tiptap-extensions'
import 'quasar-tiptap-branch/lib/index.css'

export default {
  data () {
    return {
      options: {
        content: 'content',
        editable: true,
        extensions: [
            ...RecommendedExtensions,
            new Placeholder({
              showOnlyCurrent: false,
              emptyNodeText: node => {
                if (node.type.name === 'title') {
                  return 'Title'
                }
                return 'Content'
              }
            })
          ],
        toolbar: [
          'add-more',
          'separator',
          'bold',
          'italic',
          'underline',
          // other toolbar buttons
          // name string
        ]
      },
      json: '',
      html: ''
    }
  },
  components: {
    QuasarTiptap,
  },
  methods: {
    onUpdate ({ getJSON, getHTML }) {
      this.json = getJSON()
      this.html = getHTML()
      console.log('html', this.html)
    }
  }
}
</script>
```

## Editor Properties And Others

The other details please see [quasar-tiptap](https://github.com/donotebase/quasar-tiptap)

## Thanks

- Authors of [Quasar Framework](https://github.com/quasarframework)
- Authors of [tiptap](https://github.com/scrumpy/tiptap)
- Authors of [quasar-tiptap](https://github.com/donotebase/quasar-tiptap)
- Leecason for [element-tiptap](https://github.com/Leecason/element-tiptap)

## License

The MIT License (MIT). Please see [License File](https://github.com/rdminfo/quasar-tiptap-branch/blob/dev/README.md) for more information.
