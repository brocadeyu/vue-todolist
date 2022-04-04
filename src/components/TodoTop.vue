<template>
  <div class="top">
    <el-input value="666" placeholder="请输入内容"></el-input>
    <el-button @click="handleClick">添加</el-button>
  </div>
</template>

<script>
export default {
  name: 'TodoTop',
  props: {
    msg: String
  },
  methods:{
    handleClick(e){
      e.target.blur()
      e.target.parentNode.blur();
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
