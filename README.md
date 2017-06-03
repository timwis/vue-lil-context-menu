# vue-context

A flexible context menu component for Vue. Pass it any menu template you like;
it doesn't even have to be a menu. Always disappears when you expect it
to by using an `onblur` event.

```html
<div @contextmenu.prevent="$refs.menu.open">
  ...
</div>

<context-menu ref="menu">
  <ul class="menu">
    <li @click="onClick('A')">Option A</li>
    <li @click="onClick('B')">Option B</li>
  </ul>
</context-menu>

<script>
const contextMenu = require('vue-context')

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
.menu {
  width: 250px;
  border: 1px black solid;
}
</style>
```

## Related
- [vue-context-menu](https://github.com/vmaimone/vue-context-menu)
