<template>
  <el-container class="container">
    <el-header class="header">
      <el-row>
        <el-col :span="4">
          <div class="grid-content bg-purple">
            <!-- <img src="../../assets/logo.png" alt="无法显示图片" /> -->
          </div>
        </el-col>
        <el-col :span="18" class="middle">
          <h2>后台管理系统</h2>
        </el-col>
        <el-col :span="28">
          <div class="grid-content bg-purple">
            <a href="#" class="loginout" @click.prevent="handleSignout">退出</a>
          </div>
        </el-col>
      </el-row>
    </el-header>
    <el-container>
      <el-aside class="aside" width="200px">
        <!--侧面导航-->
        <el-menu
        :unique-opened=true>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>用户管理</span>
            </template>
            <el-menu-item index="1-1">
              <i class="el-icon-s-grid"></i>
              <span>用户列表</span>
            </el-menu-item>
          </el-submenu>
          <!--guide 2-->
          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>权限管理</span>
            </template>
            <el-menu-item index="2-1">
              <i class="el-icon-s-grid"></i>
              <span>角色列表</span>
            </el-menu-item>
            <el-menu-item index="2-2">
              <i class="el-icon-location"></i>
              <span>权限列表</span>
            </el-menu-item>
          </el-submenu>
          <!--guide 3-->
          <el-submenu index="3">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>商品管理</span>
            </template>
            <el-menu-item index="3-1">
              <i class="el-icon-location"></i>
              <span>商品列表</span>
            </el-menu-item>
            <el-menu-item index="3-2">
              <i class="el-icon-location"></i>
              <span>分类参数</span>
            </el-menu-item>
            <el-menu-item index="3-3">
              <i class="el-icon-location"></i>
              <span>商品分类</span>
            </el-menu-item>            
          </el-submenu>
          <!--guide 4-->
          <el-submenu index="4">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>订单管理</span>
            </template>
            <el-menu-item index="4-1">
              <i class="el-icon-location"></i>
              <span>订单列表</span>
            </el-menu-item>
          </el-submenu>
          <!--guide 5-->
          <el-submenu index="5">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>数据统计</span>
            </template>
            <el-menu-item index="5-1">
              <i class="el-icon-location"></i>
              <span>数据报表</span>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main class="main">Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
    //保证有token才能继续渲染
    beforeCreate() {
        const token = localStorage.getItem('token')
        console.log(token)
        if(!token) {
            this.$router.push({name:'login'})
        }
    },
    methods : {
        handleSignout() {
            localStorage.clear()
            this.$message.success("退出成功")
            this.$router.push({name: 'login'})

        }
    }
};
</script>

<style>
.container {
  height: 100%;
  background-color: #b3c0d1;
}
.header {
  background-color: #d3dcd6;
}
.main {
  background-color: #e9eef3;
}

/*头部样式 */
.middle {
  text-align: center;
}
.middle h2 {
    margin-top: 14px;
}
.loginout {
  line-height: 60px;
  text-decoration: none;
}
</style>