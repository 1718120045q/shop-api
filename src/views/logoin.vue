<template>
  <el-row type="flex" justify="center" align="middle" class="row-bg" >
    <el-col :span="8" class="row-son">
      <el-form ref="form" :model="form" label-width="80px" :rules="rules" >
        <el-form-item label="用户名" prop="username">
          <el-input v-model="form.username"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input v-model="form.password"></el-input>
        </el-form-item>
        <el-form-item>
            <el-button type="primary" @click="submitForm('form')">登录</el-button>
            <el-button type="info">重置</el-button>
        </el-form-item>
      </el-form>
    </el-col>
  </el-row>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
      form: {
        username:"",
        password:"",
        
      },
      rules:{
         username: [
              {
                  required: true, message: '请输入用户名', trigger: 'blur'
              },
              { min: 5, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
          ],
          password: [
              {
                  required: true, message: '请输入密码', trigger: 'blur'
              },
              { min: 6, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
              
          ]
      }
    };
  },
methods:{
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
              axios({
                  url:'http://localhost:8888/api/private/v1/login',
                  method:'post',
                  data:this.form
                      
                  
              }).then(({data: {data, meta}}) => {
                  if(meta.status===200){
                      localStorage.setItem("token",data.token);
                      this.$router.push("/home")
                  }
              })
          } 
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
<style>
    .row-bg{
        height: 100%;
        background-color: #2D434C;
    }
    .row-son{
        background-color: #fff;
        padding: 30px 20px;
        /* text-align: center; */
        /* height: 200px; */
        border-radius: 20px
    }
</style>
