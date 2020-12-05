<template>
  <div class="main">
    <div class="bg"></div>
    <div class="page">
      <div>
        <img src="../assets/logo.png" />
      </div>
      <el-form
        ref="loginForm"
        :model="user"
        :rules="rules"
        status-icon
        label-width="70px"
      >
        <el-form-item label="用户名" prop="name">
          <el-input v-model="user.name"> </el-input>
        </el-form-item>
        <el-form-item label="密码" prop="pass">
          <el-input v-model="user.pass" type="password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" icon="el-icon-upload" @click="login"
            >登录
          </el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      user: {
        name: "",
        pass: "",
        openid: "",
      },
      rules: {
        name: [{ required: true, message: "用户名不能为空", trigger: "blur" }],
        pass: [{ required: true, message: "密码不能为空", trigger: "blur" }],
      },
    };
  },
  methods: {
    login() {
      this.$refs.loginForm.validate((valid) =>{
        if(valid) {
          if(this.user.name === 'admin' && this.user.pass === '123456') {
            this.$router.replace('/')
          }
        }
        else {
          this.$notify({
            type: 'error',
            message: '用户名或密码错误',
            showClose: true
          })
          console.log('123')
        }
      })
    }
  }
};
</script>

<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.main {
  width: 99vw;
  height: 95vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.bg {
  width: 100%;
  height: 100%;
  background: url("https://class.elab-dlut.cn/imgs/timg.jpg") no-repeat;
  position: absolute;
  background-size: cover;
}

.page {
  width: 400px;
  height: 400px;
  position: relative;
  background-color: rgba(255, 255, 255, 0.6);
  border-radius: 8px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
  overflow: hidden;
  z-index: 2;
  padding: 30px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
</style>