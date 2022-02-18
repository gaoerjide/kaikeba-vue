<template>
  <div class="admin">
    <message ref="msgSuccess"
             class="success">
      <template v-slot:title="slotProps">
        <strong>{{slotProps.title}}</strong>
      </template>
      <!-- 默认插槽 -->
      <template v-slot:default>
        新增课程成功！
      </template>
    </message>
    <message ref="msgWarning"
             class="warning">
      <!-- 命名为title的插槽 -->
      <!-- <template v-slot:title> -->
      <template v-slot:title>
        <strong>警告</strong>
      </template>
      <!-- 默认插槽 -->
      <template v-slot:default>
        请输入课程的名称！
      </template>

    </message>

    <!-- 新增课程 -->
    <CourseAdd v-model="course"
               @add-course="addCourse"></CourseAdd>
    <CourseList :courses="courses"></CourseList>

    <!-- 嵌套内容的出口 -->
    <router-view></router-view>
  </div>
</template>

<script>
import CourseList from '@/components/CourseList.vue'
import CourseAdd from '@/components/CourseAdd.vue'
import Message from '@/components/Message.vue'
import {
  getCourses
} from '@/api/course.js'
export default {
  name: 'admin',
  components: {
    CourseList,
    CourseAdd,
    Message
  },
  data () {
    return {
      title: '开课吧购物车',
      course: '',
      courses: []
    }
  },
  async created () {
    // 组件实例已创建，由于未挂载，dom不存在
    const courses = await getCourses()
    this.courses = courses
  },
  methods: {
    addCourse () {
      if (this.course) {
        this.courses.push({
          name: this.course
        })
        this.course = ''
        this.$refs.msgSuccess.togger()
      } else {
        this.$refs.msgWarning.togger()
      }

    },
  },
  activated () {
    console.log('active');
  },
  deactivated () {
    console.log('deactive');
  },
  // beforeRouteEnter (to, from, next) {
  //   //用户是否登录
  //   if (window.isLogin) {
  //     next()
  //   } else {
  //     next('/login?redirect=' + to.fullPath)
  //   }

  // }
}
</script>
