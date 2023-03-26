<template>
  <el-form
    ref="ruleFormRef"
    :model="ruleForm"
    :rules="rules"
    label-width="120px"
    class="demo-ruleForm"
    :size="formSize"
    status-icon
  >
    <el-form-item label="用户名" prop="username" width="20vw">
      <el-input v-model="ruleForm.username" />
    </el-form-item>
    <el-form-item label="用户昵称" prop="nickname">
      <el-input v-model="ruleForm.nickname" />
    </el-form-item>
    <el-form-item label="用户密码" prop="password">
      <el-input v-model="ruleForm.password" />
    </el-form-item>
    <el-form-item label="手机号码" prop="phone">
      <el-input v-model="ruleForm.phone" />
    </el-form-item>
    <el-form-item label="邮箱" prop="email">
      <el-input v-model="ruleForm.email" />
    </el-form-item>
    <el-form-item label="性别" prop="male">
      <el-select v-model="ruleForm.male">
        <el-option label="男" value="male" />
        <el-option label="女" value="female" />
      </el-select>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm(ruleFormRef)"> Create </el-button>
      <el-button @click="resetForm(ruleFormRef)">Reset</el-button>
    </el-form-item>
  </el-form>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'
import CryptoJS from 'crypto-js'

const md5 = (str) => CryptoJS.MD5(str).toString().toUpperCase()

const formSize = ref('default')
const ruleFormRef = ref<FormInstance>()
const ruleForm = reactive({
  username: '',
  nickname: '',
  password: '',
  phone: '',
  email: '',
  male: ''
})

const rules = reactive<FormRules>({
  username: [
    { required: true, message: 'Please input username', trigger: 'blur' },
    { min: 3, max: 20, message: 'Length should be 3 to 20', trigger: 'blur' }
  ],
  nickname: [
    { required: true, message: 'Please input nickname', trigger: 'blur' },
    { min: 3, max: 20, message: 'Length should be 3 to 20', trigger: 'blur' }
  ],
  password: [
    { required: true, message: 'Please input password', trigger: 'blur' },
    { min: 3, max: 20, message: 'Length should be 3 to 20', trigger: 'blur' }
  ]
})

const submitForm = async (formEl: FormInstance | undefined) => {
  if (!formEl) return
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log('submit!')
      var registerSubmit = Object.assign({}, ruleForm)
      registerSubmit.password = md5(ruleForm.password)
      console.log(registerSubmit)
    } else {
      console.log('error submit!', fields)
    }
  })
}

const resetForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.resetFields()
}

const options = Array.from({ length: 10000 }).map((_, idx) => ({
  value: `${idx + 1}`,
  label: `${idx + 1}`
}))
</script>

<style scoped>
.el-form-item {
  margin-left: 10%;
  width: 60%;
}
.el-form {
  width: 50vw;
  height: 60vh;
  margin-left: 25%;
  padding-top: 2%;
  background-color: aliceblue;
  border-radius: 16px;
}
</style>
