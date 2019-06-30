<template>
  <el-container>
    <el-header>
      <el-row type="flex" class="row-bg" justify="space-between" align="middle">
        <el-col :span="6">
          <img src="../assets/logo.png" alt>
        </el-col>
        <el-col>
          <div class="grid-content bg-purple-light">
            <h1>品优购后台管理系统</h1>
          </div>
        </el-col>
        <el-col :span="6">
          <div class="grid-content bg-purple">
            欢迎三十九期星耀会员
            <a href="javaScript:;">退出</a>
          </div>
        </el-col>
      </el-row>
      
    </el-header>
    <el-container>
      <el-aside width="200px">
          <el-menu
        :default-active="$router.path"
        class="el-menu-vertical-demo"
        router
        background-color="#545c64"
        text-color="#fff"
        active-text-color="#ffd04b"
        unique-opened
      >
        <el-submenu index="1">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>用户管理</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="/user">
              <i class="el-icon-menu"></i>用户管理
            </el-menu-item>
          </el-menu-item-group>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>权限管理</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>角色列表
            </el-menu-item>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>权限列表
            </el-menu-item>
          </el-menu-item-group>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>商品管理</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>商品列表
            </el-menu-item>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>分类参数
            </el-menu-item>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>商品分类
            </el-menu-item>
          </el-menu-item-group>
        </el-submenu>
        <el-submenu index="4">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>订单管理</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>订单列表
            </el-menu-item>
          </el-menu-item-group>
        </el-submenu>
        <el-submenu index="5">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>数据统计</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="1-1">
              <i class="el-icon-menu"></i>数据报表
            </el-menu-item>
          </el-menu-item-group>
        </el-submenu>
      </el-menu>
      </el-aside>
      <el-main>
        <router-view></router-view>
      </el-main>
    </el-container>
  </el-container>
</template>
<style scoped>
.row-bg {
  height: 60px;
  background-color: #b3c1cd;
  text-align: center;
}
.row-bg img {
  width: 200px;
  padding: 0;
  margin: 0;
  float: left;
}
.grid-content.bg-purple-light {
  color: #fff;
}
.grid-content.bg-purple {
  font-weight: 700;
}
.grid-content.bg-purple a {
  color: orange;
}
.el-container .el-header{
    margin: 0;
    padding: 0;
}
.el-container,.el-asidem,.el-menu{
    height: 100%;
}

</style>

