<template>
  <div ref="wrapper">
    <div>
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  // vue里面 组件 感知不到slot的变化,slot的内容发生变化组件感知不到,
  // slot的变化取决于数据的变化,
  // vue里面 组件 是可以感觉到数据的变化的,让组件接收数据就好了
  props: ['data'],
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },

  watch: {
    data () {
      this.$nextTick(() => {
        this.scroll.refresh()
      })
    }
  }
}
</script>

<style scoped>

</style>
