<template>
  <el-container class="main_container">
    <el-header>
      <div class="left_header">
        <img src="https://ae01.alicdn.com/kf/U0081623e4b9c40bb9c3426743821f96aj.jpg" />
        <span>若离今日校园签到系统</span>
      </div>
      <div class="right_header">
        <el-dropdown>
          <div class="dropbtn">
            <img src="//inews.gtimg.com/newsapp_match/0/12545892462/0" alt />
            <span>admin</span><i class="el-icon-arrow-down el-icon--right"></i>
          </div>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item icon="el-icon-edit" command="a">修改密码</el-dropdown-item>
            <el-dropdown-item icon="el-icon-s-fold" command="b">退出系统</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </el-header>
    <el-container>
      <el-aside :width="left_size + 'px'">
        <div class="menu_btn" @click="toggle_menu">{{toggle_text}}</div>
        <!-- 左边导航区域 -->
        <el-menu default-active="1-4-1" class="el-menu-vertical-demo"
          :collapse="isCollapse"
          collapse-transition=true
          background-color="#66BBFF"
          text-color="#Fff"
          active-text-color="#FFA500"
          unique-opened=true>
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <span slot="title">分组一</span>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="1-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="1-4">
              <span slot="title">选项4</span>
              <el-menu-item index="1-4-1">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>

          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <span slot="title">分组一</span>
              <el-menu-item index="2-1">选项1</el-menu-item>
              <el-menu-item index="2-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="2-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="2-4">
              <span slot="title">选项4</span>
              <el-menu-item index="2-4-1">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main>Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
  export default {
    name: 'main',
    data() {
      return {
        isCollapse: false,
        left_size: 220,
        toggle_text: '<<<'
      }
    },
    methods: {
      toggle_menu() {
        this.isCollapse = !this.isCollapse;
        this.left_size = this.left_size==220?66:220;
        this.toggle_text = this.toggle_text == '<<<'?'>>>':'<<<';
      }

    }
  }
</script>

<style lang="less" scoped>
  .main_container {
    height: 100%;
  }

  // 头部布局
  .el-header {
    padding-left: 0;
    background-color: #66BBFF;
    color: #FFF;
    line-height: 60px;
    display: flex;
    justify-content: space-between;

    .left_header {
      align-items: center;
      display: flex;

      img {
        height: 60px;
        margin-left: 0;
        width: 220px;
      }

      span {
        margin-left: 15px;
        font-size: 22px;
        font-weight: bold;
      }
    }

    .right_header:hover {
      cursor: pointer !important;
    }

    .dropbtn {
      height: 60px;
      display: flex;
      align-items: center;
      img {
        width: 40px;
        height: 40px;
        border-radius: 50%;
      }

      span {
        margin-left: 10px;
        font-size: 18px;
        color: #fff;
      }

      .dropbtn:active,
      .dropbtn:visited {
        outline: none;
      }
    }

  }

  // 左边导航
  .el-aside {
    background-color: #66BBFF;
    transition: .4s;
    .el-menu {
      border-right-width: 0;
    }
    .menu_btn {
      color: #fff;
      text-align: center;
      font-size: 18px;
      line-height: 26px;
      cursor: pointer;
      letter-spacing: -8px;
      transform: scale(1,2);
    }
  }

  // 主区域
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }

  body>.el-container {
    margin-bottom: 40px;
  }
</style>
