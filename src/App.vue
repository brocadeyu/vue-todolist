<template>
  <div id="container">
    <div id="app">
      <TodoTop/>
      <TodoList :todos="todos"  />
      <TodoFoot/>
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
      todos:[
        {title:'学习',id:1,done:false},
        {title:'看书',id:2,done:true},
        {title:'游戏',id:3,done:false},
        {title:'写字000',id:5,done:false},
        {title:'写字000',id:6,done:false},
        {title:'写字000',id:7,done:false},
        {title:'写字000',id:8,done:false},
        {title:'写字000',id:9,done:false},
        {title:'写字00',id:10,done:true},

      ]
    }
  },
  methods:{
    addTodo(x){
      this.todos.unshift(x)
    }

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
