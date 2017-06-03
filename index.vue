<template>
  <div
    v-show="isVisible"
    class="lil-context-menu"
    :style="style"
    tabindex="-1"
    @blur="close"
    @click.capture="close"
    @contextmenu.capture.prevent>
    <slot></slot>
  </div>
</template>

<script>
const Vue = require('vue')

module.exports = {
  name: 'lil-context-menu',
  data () {
    return {
      x: null,
      y: null
    }
  },
  computed: {
    style () {
      return this.isVisible ? {
        top: this.y - document.body.scrollTop + 'px',
        left: this.x + 'px'
      } : {}
    },
    isVisible () {
      return this.x !== null && this.y !== null
    }
  },
  methods: {
    open (evt) {
      this.x = evt.pageX || evt.clientX
      this.y = evt.pageY || evt.clientY
      Vue.nextTick(() => this.$el.focus())
    },
    close (evt) {
      this.x = null
      this.y = null
    }
  }
}
</script>

<style scoped>
.lil-context-menu {
  position: fixed;
  z-index: 999;
}
.lil-context-menu:focus {
  outline: none;
}
</style>
