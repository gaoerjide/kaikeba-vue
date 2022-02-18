<template>
  <div id="app">
    <!-- 导航链接 -->
    <nav>
      <router-link to="/">首页</router-link>
      <router-link to="/admin">管理</router-link>
    </nav>
    <!-- 路由出口 -->
    <keep-alive include="admin">
      <router-view></router-view>
    </keep-alive>
  </div>
</template>

<script>


//总线
// Vue.prototype.$bus = new Vue();
export default {
  name: 'app',

}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
.success {
  background: #4fc08d;
  border: 1px solid #42b983;
}

.warning {
  background: #f66;
  border: 1px solid #d63200;
}
</style>
