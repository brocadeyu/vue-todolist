<template>
  <div class="top">
    <el-input v-model="inputValue" placeholder="请输入内容"></el-input>
    <el-button @click="handleAdd">添加</el-button>
  </div>
</template>

<script>
import {nanoid} from 'nanoid'
export default {
  name: 'TodoTop',
  methods:{
    handleAdd(e){
      e.target.blur()
      e.target.parentNode.blur();
      if(!this.inputValue) return this.$message('请输入内容');
      const todoObj={
        title:this.inputValue,
        id:nanoid(),
        done:false
      }
      this.$bus.$emit('addTodo',todoObj)
      this.inputValue=''
    }
  },
  data(){
    return {
      inputValue:''
    }
  }
}
</script>

<style scoped>
.top{
  margin:auto;
  justify-content: center;
  display: flex;
}
button{
  margin-left: 10px;
}
</style>
