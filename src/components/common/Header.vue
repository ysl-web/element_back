<template>
    <el-container class="header">
      <el-header>
        <p>aaa</p>
      </el-header>
    </el-container>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style lang="scss">
  .header{
    position: fixed;
    top: 0;
    left: 201px;
    width: calc(100% - 201px);
    background: #fff;
    z-index: 999;
  }
</style>