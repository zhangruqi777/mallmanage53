<template>
  <div class="login-wrap">
    <el-form class="login-form" label-position="top" label-width="80px" :model="formdata">
      <h2>用户登录</h2>
      <el-form-item label="用户名">
        <el-input v-model="formdata.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="formdata.password"></el-input>
      </el-form-item>
      <el-button class="login-btn" type="primary" @click="handleLogin">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      formdata: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    //登录请求
    // async handleLogin() {
    //   const vm = this
    //   //希望让这里异步的代码看起来像同步代码,使用了async+await，这里没有箭头函数，this都不对
    //   const response= await this.$http.post('login',this.formdata) 
    //   //解构赋值
    //   // const {data,meta:{msg,status}} =response.data
    //   const res = response.data
    //   const data = res.data
    //   const meta = res.meta
    //   const status = meta.status
    //   if(status === 200) {
    //      vm.$message.success(meta.msg)
    //      vm.$router.push({name: 'home'})
    //   } else {
    //      vm.$message.warning(meta.msg)
    //   }      
    // }
    // handleLogin(){
    //   this.$http.post('login',this.formdata).then(response=>{
    //     const {data,meta:{msg,status}} =response.data
    //     if(status === 200){
    //       this.$message.success(msg)
    //     }
    //   })
    // }
    async handleLogin(){
      const response = await this.$http.post('login',this.formdata)
      const {data,meta:{msg,status}} =response.data
      if(status === 200){
        //0.保存token,如果用户没有登陆直接来到home组件，要判断用户是否登陆过
        localStorage.setItem('token',data.token)
        console.log(localStorage.getItem('token'))
        //1.跳转home
        this.$router.push({name:'home'})
        this.$message.success(msg)
      }else {
        this.$message.error(msg)
      }
    }
  }
}
</script>

<style>
.login-wrap {
    height: 100%;
    background-color: #324152;
    display: flex;
    justify-content: center;
    align-items: center;
}
.login-wrap .login-form {
    width: 400px;
    background-color: #fff;
    border-radius: 5px;
    padding: 30px;
}
.login-wrap .login-btn {
    width: 100%;
}
</style>
