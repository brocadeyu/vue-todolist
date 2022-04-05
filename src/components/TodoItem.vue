<template>
  <div class="todoitem">
    <el-checkbox v-model="checked" @change="handleCheck(todo.id)" >
     
      <el-input v-model="inputValue" v-show="todo.isEdit" ref="buttonFocus" placeholder="请输入内容" size="mini" @blur="handleBlur(todo)">
      </el-input>
    </el-checkbox>
     <span v-show="!todo.isEdit">
        {{todo.title}}
      </span>
    <el-button  type="success"  size="small" @click="handleCheck1(todo.id)">完成</el-button>
    <el-button  type="danger" size="small" @click="handleDelete(todo.id)">删除</el-button>
    <el-button  type="primary" size="small" @click="handleEdit(todo)" >编辑</el-button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  data(){
    return {
      checked:this.todo.done,
      inputValue:''
    }
  },
  methods:{
    handleCheck(x){
      this.$bus.$emit('statusTodo',x)
    },
    handleDelete(x){
      this.$bus.$emit('deleteTodo',x)
    },
    handleEdit(todo){
      this.$set(todo,'isEdit',true)
      this.inputValue=this.todo.title
      this.$nextTick(function () {
         this.$refs.buttonFocus.$el.querySelector('input').focus();
     });
    },
    handleBlur(todo){
         this.$bus.$emit('editTodo',todo,this.inputValue)
      todo.isEdit=false
   
    },
    handleCheck1(x){
      this.$bus.$emit('statusTodo',x)
      this.checked=!this.checked
    }
  }
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
.el-input{
  width:100px
}
.todoitem:hover button  {
 display: inline-block;

}
/* .el-checkbox{
  visibility: hidden;
}
.todoitem:hover .el-checkbox {
 visibility: inherit;

} */





</style>
