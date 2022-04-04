<template>
  <div class="todoitem">
    <el-checkbox :checked="todo.done">{{todo.title}}</el-checkbox>
    <el-button @click="handleClick" type="success"  size="small" >完成</el-button>
    <el-button @click="handleClick" type="danger" size="small" >删除</el-button>
    <el-button @click="handleClick" type="primary" size="small" >编辑</el-button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo']
}
</script>

<style scoped>
.todoitem{
  line-height: 30px;
  width:400px;
  height: 30px;
  margin: 10px auto;
  padding: 5px 5px;
}
.el-button{
 display: none;
 float: right;
 margin-left: 10px;
}

.todoitem:hover button {
 display: inline-block;

}





</style>
