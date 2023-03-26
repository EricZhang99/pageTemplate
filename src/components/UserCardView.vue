<script setup>
import router from '../router'
var showCard = true
function gotoUserPage() {
  router.push('/user')
}
</script>

<template>
  <el-popover
    :width="300"
    popper-style="box-shadow: rgb(14 18 22 / 35%) 0px 10px 38px -10px, rgb(14 18 22 / 20%) 0px 10px 20px -15px; padding: 20px;"
    trigger="click"
  >
    <template #reference>
      <el-avatar
        src="https://robohash.org/eric"
        :size="100"
        style="max-height: 10vh; max-width: 10vh"
      />
      <!-- <el-icon style="padding-left: 40vw; padding-right: 40vw"><HomeFilled /></el-icon> -->
    </template>

    <template #default>
      <div class="demo-rich-conent" style="display: flex; gap: 16px; flex-direction: column">
        <div class="userInfo" v-if="showCard">
          <el-row>
            <el-avatar
              :size="60"
              src="https://robohash.org/eric"
              style="margin-bottom: 8px; margin-top: 8px"
            />
            <p
              class="demo-rich-content__name"
              style="
                margin: 0;
                font-weight: 100;
                font-size: 30px;
                padding-top: 10px;
                padding-left: 5px;
              "
            >
              eric
            </p>
          </el-row>
          <el-divider />
          <el-row>
            <el-col :span="6">
              <el-statistic title="作品数量" :value="12" />
            </el-col>
            <el-col :span="6">
              <el-statistic title="好友人数" :value="2" />
            </el-col>
            <el-col :span="6">
              <el-statistic title="关注人数" :value="4" />
            </el-col>
          </el-row>
          <el-divider />
          <el-row>
            <p class="demo-rich-content__desc" style="margin: 0; padding-top: 5px">
              反正火车总得创死一个，那就创死你吧。
            </p>
          </el-row>
          <el-divider />
          <el-row>
            <el-button
              type="primary"
              style="padding-left: 40%; padding-right: 40%"
              round
              @click="gotoUserPage"
              >前往主页</el-button
            >
          </el-row>
        </div>
        <div class="toLaunch" v-else>
          <p>please login or register</p>
          <el-button type="success" round><RouterLink to="/login">点击登陆</RouterLink></el-button>
          <el-button type="primary" round
            ><RouterLink to="/register">点击注册</RouterLink></el-button
          >
        </div>
      </div>
    </template>
  </el-popover>
</template>

<style scoped>
.router-link-active {
  text-decoration: none;
  color: aliceblue;
}
a {
  text-decoration: none;
  color: aliceblue;
}
</style>
