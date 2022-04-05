<template>
  <div id="container">
    <div id="app">
      <TodoTop/>
      <TodoList :todos="todos"  />
      <TodoFoot :todos="todos" :checkAllTodo="checkAllTodo" :deleteDone="deleteDone"/>
    </div>
  </div>
</template>

<script>
import TodoTop from './components/TodoTop.vue'
import TodoList from './components/TodoList.vue'
import TodoFoot from './components/TodoFoot.vue'

export default {
  name: 'App',
  components: {
    TodoTop,TodoList,TodoFoot
  },
  data(){
    return {
      todos:JSON.parse(localStorage.getItem('todos')) || [
        {title:'吃饭',id:1,done:true},
        {title:'睡觉',id:2,done:false},
        {title:'代码',id:3,done:true},
        {title:'本地存储，隐私++',id:4,done:true},
      ]
    }
  },
  methods:{
    addTodo(x){
      this.todos.unshift(x)
    },
    editTodo(data,x){
      this.todos.forEach((todo)=>{
        if(todo.id===data.id)
        todo.title=x
      })
    },
    deleteTodo(x){
      this.todos=this.todos.filter((todo)=>{
        return todo.id!=x
      })
    },
    deleteDone(){
      this.todos=this.todos.filter((todo)=>{
        return todo.done==false
      })
    },
    checkAllTodo(x){
      this.todos.forEach((todo)=>{
        todo.done=x
      })
    },
    statusTodo(x){
      this.todos.forEach((todo)=>{
        if(todo.id===x)
        todo.done=!todo.done
      })
    }
  },
  watch:{
    todos:{
      deep:true,
      handler(value){
        localStorage.setItem('todos',JSON.stringify(value))
      }
    }
  },
  mounted(){
    this.$bus.$on('addTodo',(data)=>{
      this.addTodo(data);
    })
    this.$bus.$on('statusTodo',(data)=>{
      this.statusTodo(data);
    })
    this.$bus.$on('deleteTodo',(data)=>{
      this.deleteTodo(data);
    })
    this.$bus.$on('editTodo',(data,x)=>{
      this.editTodo(data,x);
    })
    this.todos.forEach((todo)=>{
      if(todo.isEdit){
         todo.isEdit=false
     this.$message('请重新输入')
      }
    
    })
  },
  beforeDestroy(){
    this.$bus.$off('addTodo')
    this.$bus.$off('statusTodo')
    this.$bus.$off('deleteTodo')
  }
}
</script>

<style>
#app {
 padding: 30px;
}
#container {
 width:500px;
 margin:auto;
 margin-top: 50px;
 border: 1px solid rgb(175, 175, 175) ;
 border-radius: 10px;
}

</style>
