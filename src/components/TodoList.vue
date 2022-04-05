<template><div class="main">
  <el-divider content-position="center">待办事项</el-divider>
  <TodoItem v-for="todo in todos"  :key="todo.id" :todo="todo" />
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
  name: 'TodoList',
  props: ['todos'],
  components:{
    TodoItem
  }
}
</script>

<style scoped>
.main{
  width: 100%;
  height: 100%;
  margin-top: 30px;
  /* border:1px solid;
  border-radius: 10px; */

}

</style>
