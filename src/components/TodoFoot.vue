<template>
 <div>
   <el-empty description="空空如也" v-show="!todoLength"></el-empty>
    <div class="foot" v-show="todoLength">
  <el-checkbox :value="isAll" @change="checkAll()">全选</el-checkbox>
  <span>已完成： {{doneTodo}} / 合计： {{todoLength}}</span> 
      <el-button  size="small" @click="handleDeleteDone">删除已完成</el-button>
  </div>
 </div>
</template>

<script>
export default {
  name: 'TodoFoot',
  props: ['todos','checkAllTodo','deleteDone'],
  computed:{
    todoLength(){
      return this.todos.length
    },
    doneTodo(){
      let i = 0
      this.todos.forEach((todo)=>{
        if(todo.done){
          i++
        }
      })
      return i
    },
    isAll(){
      return this.todoLength===this.doneTodo&&this.todoLength>0
    }
  },
  methods:{
    checkAll(){
      this.checkAllTodo(!this.isAll)
    },
    handleDeleteDone(){
      this.deleteDone()
    }
  }
}
</script>

<style scoped>
.foot{
  margin-top: 30px;

}

label input  {
  float: left;
}
span{
  margin: 0 65px;
}
</style>
