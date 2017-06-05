# vue-lil-context-menu

A flexible context menu component for Vue. Pass it any menu template you like;
it doesn't even have to be a menu. Always disappears when you expect it
to by using an `onblur` event.

```html
<div @contextmenu.prevent="$refs.menu.open">
  ...
</div>

<context-menu ref="menu">
  <ul class="options">
    <li @click="onClick('A')">Option A</li>
    <li @click="onClick('B')">Option B</li>
  </ul>
</context-menu>

<script>
const contextMenu = require('vue-lil-context-menu')

module.exports = {
  components: {
    'context-menu': contextMenu
  },
  methods: {
    onClick (opt) {
      console.log('Clicked', opt)
    }
  }
}
</script>

<style scoped>
.options {
  width: 250px;
  border: 1px black solid;
}
</style>
```

If you'd like to pass any context from the original `oncontextmenu`
event down to your menu template, you can pass it as the second
param of `open` and access it within a [scoped slot](https://vuejs.org/v2/guide/components.html#Scoped-Slots)
under the `userData` property. For example:

```html
<div @contextmenu.prevent="$refs.menu.open($event, 'foo')">
  ...
</div>

<context-menu ref="menu">
  <template scope="child">
    <li @click="onClick('A', child.userData)">Option A</li>
    <li @click="onClick('B', child.userData)">Option B</li>
  </template>
</context-menu>
```

## Related
- [vue-context-menu](https://github.com/vmaimone/vue-context-menu)
