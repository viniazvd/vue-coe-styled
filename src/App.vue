<script>
export default {
  name: 'vue-coe-styled',

  data () {
    return { color: 'red' }
  },

  style (vm) {
    const title = vm => vm.color

    return { '--title': title(vm) }
  },

  render (h) {
    const title = h('h1', { style: (this.$options.style(this)) }, 'coe')

    const input = [ h('input', {
      domProps: { value: this.color },
      on: { input: event => { this.color = event.target.value } }
    }) ]

    return h('div', { attrs: { id: 'app' } }, [ title, input ])
  }
}
</script>

<style lang="scss">
h1 { color: var(--title); }
</style>
