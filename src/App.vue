<template>
  <div id="app">
    <div class="nav">
      <el-row class="tac">
        <el-col>
          <el-menu
            default-active="2"
            class="el-menu-vertical-demo"
            unique-opened
            @open="handleOpen"
            @close="handleClose"
          >
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>数据核实</span>
              </template>
              <el-menu-item index="1-1">
                <router-link to="/">任务分配</router-link>
              </el-menu-item>
              <el-menu-item index="1-2">
                <router-link to="/about">任务统计</router-link>
              </el-menu-item>
            </el-submenu>
            <el-submenu index="2">
              <template slot="title">
                <i class="el-icon-menu"></i>
                <span>标准地址</span>
              </template>
              <el-menu-item index="2-1">标准地址管理</el-menu-item>
              <el-menu-item index="2-2">警务区批量修改</el-menu-item>
              <el-menu-item index="2-3">人员联系方式修改</el-menu-item>
              <el-menu-item index="2-4">查询日志</el-menu-item>
            </el-submenu>
            <el-submenu index="3">
              <template slot="title">
                <i class="el-icon-menu"></i>
                <span>统计分析</span>
              </template>
              <el-menu-item index="3-1">单位工作量统计</el-menu-item>
              <el-menu-item index="3-2">个人工作量统计</el-menu-item>
              <el-menu-item index="3-3">工作质量统计</el-menu-item>
              <el-menu-item index="3-4">注销人员统计</el-menu-item>
              <el-menu-item index="3-5">数据核实任务统计</el-menu-item>
            </el-submenu>
            <el-submenu index="4">
              <template slot="title">
                <i class="el-icon-menu"></i>
                <span>消息管理</span>
              </template>
              <el-menu-item index="4-1">未读消息</el-menu-item>
              <el-menu-item index="4-2">已读消息</el-menu-item>
              <el-menu-item index="4-3">已发送消息</el-menu-item>
            </el-submenu>
          </el-menu>
        </el-col>
      </el-row>
    </div>

    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>-->
    <Header></Header>
    <div class="content">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Header from '@/components/common/Header.vue'
import Home from '@/views/Home.vue'
export default {
  components: {
    Header,
    Home
  },
  data() {
    return {
      radio: '1'
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  }
};
</script>

<style lang="scss">
#app {
  position: relative;
  min-width: 1200px;

  .nav {
    position: fixed;
    top: 0;
    left: 0;
    width: 201px;
    height: 100vh;
    background: #fff;
    border-right: 1px solid #eee;
    box-sizing: border-box;
    z-index: 999;

    .el-menu {
      border: none;
    }
  }

  .content{
    position: relative;
    padding: 80px 20px 0 221px;
    z-index: 1;
  }
}
</style>
