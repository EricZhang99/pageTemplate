<script setup>
import UserCardView from './components/UserCardView.vue'
import router from './router'
function gotoIndex() {
  console.log('goto index')
  // this.$router.push('/')
  router.push({ name: 'home' })
}
</script>

<template>
  <div class="backimg">
    <div class="common-layout">
      <el-container>
        <el-header direction="horizontal">
          <el-row :gutter="24">
            <el-col :span="6">
              <UserCardView></UserCardView>
            </el-col>
            <el-col :span="12">
              <el-icon
                color="#BDE4F4"
                size="50"
                style="padding-top: 10px; margin-left: 40%"
                @click="gotoIndex"
              >
                <HomeFilled class="gohome" />
              </el-icon>
              <el-icon color="#BDE4F4" size="50" style="padding-top: 10px" @click="gotoIndex">
                <CirclePlus class="upload_video" />
              </el-icon>
            </el-col>
          </el-row>
        </el-header>
        <el-main>
          <RouterView />
        </el-main>
      </el-container>
    </div>
  </div>
</template>

<style scoped>
:root {
  border: 0;
  margin: 0;
  padding: 0;
}
.common-layout .el-container {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
  filter: blur(0);
}
.el-header {
  width: 100vw;
  height: 10vh;
  max-height: 10vh;
}
/* .el-container {
  line-height: 1.5;
  max-height: 100vh;
} */
.backimg {
  background-image: url('../public/bg-original.png');
  background-size: 100% 100%;
  background-repeat: no-repeat;
}
.el-main {
  padding-bottom: 1%;
}
</style>
