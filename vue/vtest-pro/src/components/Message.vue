<template>
  <div class="message-box"
       v-if="show">
    <!-- 具名插槽 -->
    <slot name="title"
          title="来自message的标题">默认标题</slot>
    <!-- 通过slot插槽获取传入内容 -->
    <slot></slot>
    <span class="message-box-close"
          @click="togger">X</span>
  </div>
</template>

<script>
export default {
  data () {
    return {
      show: false
    }
  },
  // mounted () {
  //   this.$bus.$on('message-close', () => {
  //     this.togger()
  //   })
  // },
  methods: {
    togger () {
      this.show = !this.show
    }
  },

}
</script>

<style scoped>
.message-box {
  padding: 10px 20px;
}

.message-box-close {
  float: right;
}
</style>