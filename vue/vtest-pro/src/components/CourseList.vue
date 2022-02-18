<template>
  <div>
    <!-- 条件渲染 -->
    <p v-if="courses.length == 0">没有任何课程信息</p>

    <!-- 列表渲染 -->
    <!-- <div v-for="c in courses" :key="c.name" 
                      :class="{active: selectedCourse === c}" @click="selectedCourse = c">
                      {{ c }}
                    </div> -->
    <!-- style -->
    <div class="course-list"
         v-else>
      <div v-for="c in courses"
           :key="c.name"
           :style="{backgroundColor: (selectedCourse === c ? '#ddd' : 'transparent')}"
           @click="onClick(c)">
        <!-- <router-link :to="`/admin/course/${c.name}`">{{ c.name }}-{{c.price | currency('$')}}</router-link> -->
        {{ c.name }}-{{c.price | currency('$')}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      selectedCourse: '',
      to: ''
    }
  },
  props: {
    courses: {
      type: Array,
      default: function () {
        return []
      }
    }

  },
  filters: {
    currency (value, symbol = '￥') {
      return symbol + value
    }
  },
  methods: {
    onClick (c) {
      this.selectedCourse = c
      // this.$router.push(`/admin/course/${c.name}`)
      this.$router.push({
        name: 'detail',
        params: {
          name: c.name
        }
      })
    }
  },
}
</script>

<style scoped>
.active {
  background-color: #ddd;
}
</style>