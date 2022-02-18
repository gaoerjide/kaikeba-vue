<template>
  <div>
    <h2>detail page</h2>
    <p>{{$route.params.name}}</p>
  </div>
</template>

<script>
export default {
  // created () {
  //   console.log('发送详情的请求');
  // }
  // watch: {
  //   $route (newValue, oldValue) {
  //     console.log('获取详情' + newValue + '---' + oldValue);//第一次的时候没有了
  //   }
  // },
  watch: {
    $route: {
      immediate: true,
      // deep: true,
      handler () {
        console.log('获取详情');
      }
    }
  },
}
</script>

<style scoped>
</style>