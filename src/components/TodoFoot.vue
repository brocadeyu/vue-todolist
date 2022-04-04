<template>
  <div class="foot">
  <el-checkbox>全选</el-checkbox>
  <span>已完成： 5 / 合计： 5</span> 
      <el-button @click="handleClick"  size="small" >删除</el-button>
  </div>
</template>

<script>
export default {
  name: 'TodoFoot',
  props: {
    msg: String
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
  margin: 0 80px;
}
</style>
