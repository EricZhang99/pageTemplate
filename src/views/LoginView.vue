<template>
  <el-form :model="formInline" class="demo-form-inline" label-width="100px">
    <el-form-item label="登陆账号" label-width="100px">
      <el-input v-model="formInline.oauth_id" placeholder="输入登陆账号" />
    </el-form-item>
    <el-form-item label="密码" label-width="100px">
      <el-input v-model="formInline.oauth_pwd" placeholder="输入登陆密码" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="onSubmit">登陆</el-button>
    </el-form-item>
  </el-form>
</template>

<script setup>
import { reactive } from 'vue'
import CryptoJS from 'crypto-js'

const md5 = (str) => CryptoJS.MD5(str).toString().toUpperCase()
const formInline = reactive({
  oauth_id: '',
  oauth_pwd: ''
})
var loginSubmit = {
  oauth_id: '',
  oauth_pwd: '',
  oauth_type: 'pwd'
}
const onSubmit = () => {
  loginSubmit.oauth_id = formInline.oauth_id
  loginSubmit.oauth_pwd = md5(formInline.oauth_pwd)
  console.log(loginSubmit)
}
</script>

<style scoped>
.el-input {
  width: 20vw;
  max-width: 150px;
  min-width: 30;
  padding-top: 10px;
}
.el-form {
  margin: auto;
  text-align: center;
  width: 30vw;
}
</style>
