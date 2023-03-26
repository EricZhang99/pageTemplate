<template>
  <div class="settingform">
    <!-- <p>用户设置界面</p> -->
    <el-upload
      class="avatar-uploader"
      action="/upload/avatar"
      :show-file-list="false"
      :on-success="handleAvatarSuccess"
      :on-error="handleAvatarError"
      :before-upload="beforeAvatarUpload"
      :limit="1"
    >
      <!-- upload 地址 ： http://domin/upload/avatar -->
      <img v-if="imageUrl" :src="imageUrl" class="avatar" />
      <el-icon v-else class="avatar-uploader-icon"><Plus /></el-icon>
    </el-upload>

    <el-form :model="sform">
      <el-form-item label="昵称" label-width="100px">
        <el-input v-model="sform.nickname" />
      </el-form-item>
      <el-form-item label="邮箱" label-width="100px">
        <el-input v-model="sform.email" placeholder="输入邮箱" />
      </el-form-item>
      <el-form-item label="手机号码" label-width="100px">
        <el-input v-model="sform.phone" placeholder="输入手机号码" />
      </el-form-item>
      <el-form-item label="性别" label-width="100px">
        <el-input v-model="sform.gender" placeholder="输入性别" />
      </el-form-item>
      <el-form-item label="自我介绍" label-width="100px">
        <el-input
          v-model="sform.script"
          style="width: 20vw"
          :rows="5"
          type="textarea"
          placeholder=""
        />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit" style="margin-left: 30%">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'
import { ElMessage } from 'element-plus'
const sform = reactive({
  nickname: '',
  email: '',
  avatar: '',
  script: '',
  phone: '',
  gender: ''
})
let fileType = ['jpeg', 'jpg', 'png']
function onSubmit() {
  console.log('submit')
  console.log(sform)
}
let imageUrl = ref('')
function handleAvatarSuccess(resp) {
  if (resp.success) {
    ElMessage.info({ dangerouslyUseHTMLString: true, message: resp.msg })
    this.sform.avatar = resp.url // 后端返给我们的路径
  } else {
    ElMessage.error('上传失败')
    console.log(resp)
  }
}

function beforeAvatarUpload(file) {
  console.log(file.type)
  console.log(file)
  if (file.type != '' || file.type != null || file.type != undefined) {
    //截取文件的后缀，判断文件类型
    const FileExt = file.name.replace(/.+\./, '').toLowerCase()
    //计算文件的大小
    const isLt5M = file.size / 1024 / 1024 < 2 //这里做文件大小限制
    //如果大于50M
    if (!isLt5M) {
      ElMessage.error('上传文件大小不能超过 2 Mb!')
      return false
    }
    //如果文件类型不在允许上传的范围内
    if (fileType.includes(FileExt)) {
      return true
    } else {
      ElMessage.error('上传文件格式不正确!')
      return false
    }
  }
}

function handleAvatarError(err) {
  console.error(err)
  ElMessage.error('上传失败')
}
</script>

<style scoped>
.settingform {
  background-color: aliceblue;
  height: 100%;
  width: 40%;
  margin-left: 30%;
  border-radius: 5%;
}
.el-input {
  width: 20vw;
}
.el-form-item {
  margin-left: 10%;
  padding-top: 10px;
}
.el-form {
  width: 40vw;
  height: 100%;
  text-align: center;
  /* margin-left: 30vw; */
}
.avatar-uploader {
  width: 100px;
  height: 100px;
  margin-left: 30%;
}
</style>
