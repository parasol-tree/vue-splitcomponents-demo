<template>
  <scroll class="css-box" :data="list">
    <div v-for="item of list" :key="item.id" class="css-con">
      {{item.text}}
    </div>
  </scroll>
</template>

<script>
import axios from 'axios'
import Scroll from '../../components/scroll/Scroll.vue'

export default {
  data () {
    return {
      list: []
    }
  },

  components: {
    Scroll
  },

  created () {
    axios.get('/api/index.json')
      .then(this.handle_get_data_success.bind(this))
      .catch(this.handle_get_data_defeat.bind(this))
  },

  methods: {
    handle_get_data_success (res) {
      const listInfo = res.data.data.detail.header.list
      this.list = listInfo
    },

    handle_get_data_defeat () {
      alert('错误')
    }
  }
}
</script>

<style scoped>
  .css-box {
    height: 100px;
    border: 1xp solid #000;
    overflow: hidden;
  }
    .css-con {
      height: 30px;
      background-color: skyblue;
      margin-bottom: 2px;
    }
</style>
