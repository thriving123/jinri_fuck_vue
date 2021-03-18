<template>
  <!-- 登陆容器 -->
  <div class="login_container">
    <!-- 登陆区域 -->
    <div class="login_box">
      <!-- 头像 -->
      <div class="avatar_box">
        <img src="//inews.gtimg.com/newsapp_match/0/12545892462/0" />
      </div>
      <!-- 表单 -->
      <el-form :model="loginForm" :rules="loginRules" ref="loginForm" class="login_Form">
        <el-form-item>
          <el-alert
              title="第一次登陆请使用智慧校园的账号密码登陆哦!"
              type="success"
              effect="dark">
            </el-alert>
          <!-- <el-tag type="success">第一次登陆请使用智慧校园的账号密码登陆哦！</el-tag> -->
        </el-form-item>
        <el-form-item prop="username">
          <el-input v-model="loginForm.username" placeholder="请输入用户名" prefix-icon="el-icon-user-solid"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input v-model="loginForm.password" placeholder="请输入密码" prefix-icon="el-icon-lock"></el-input>
        </el-form-item>
        <el-form-item class="login_btn">
          <el-button type="primary" @click="submitForm('loginForm')">登录 / 注册</el-button>
          <el-button @click="resetForm('loginForm')">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Login',
    data() {
      return {
        loginForm: {
          username: '123456',
          password: '123456',
        },
        loginRules: {
          username: [{
              required: true,
              message: '请输入登陆账号',
              trigger: 'blur'
            },
            {
              min: 4,
              max: 10,
              message: '用户名长度应该是 4 到 10 个字符',
              trigger: 'blur'
            }
          ],
          password: [{
              required: true,
              message: '请输入登陆密码',
              trigger: 'blur'
            },
            {
              min: 6,
              max: 15,
              message: '密码长度应该是 6 到 15 个字符',
              trigger: 'blur'
            }
          ]
        }
      };
      messageInfo();
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            this.$router.push('./main')
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<style lang="less" scoped>
  /* 登陆页面内部样式表 */
  // 登陆容器
  .login_container {
    height: 100%;
    background-color: aquamarine;
  }

  .login_box {
    width: 450px;
    height: 350px;
    background-color: #fff;
    border-radius: 12px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    .avatar_box {
      width: 110px;
      height: 110px;
      border-radius: 50%;
      border: 1px solid #eee;
      padding: 7px;
      box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
      margin: -55px auto;
      background-color: #fff;

      img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background-color: #eee;
      }
    }
    .login_Form{
      position: absolute;
      bottom: 5px;
      width: 100%;
      padding: 0 25px;
      box-sizing: border-box;
      .login_btn{
        display: flex;
        justify-content: flex-end;
      }
    }
  }
</style>
