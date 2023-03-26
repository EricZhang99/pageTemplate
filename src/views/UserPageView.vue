<template>
  <div class="userPage">
    <el-container>
      <el-header class="usertop">
        <div class="setting">
          <el-icon color="white" :size="30" @click="gotoSetting">
            <Setting />
          </el-icon>
        </div>
      </el-header>
      <div class="useravatar">
        <el-avatar src="https://robohash.org/eric" default="https://robohash.org/eric" />
      </div>
      <el-main class="userinfo">
        <el-row class="userdata" style="height: 20%; padding-top: 1%">
          <el-col :span="6">
            <p class="nickname">{{ nickname }}</p>
          </el-col>
          <el-col :offset="6" :span="6">
            <el-statistic title="关注数" :value="follow" group-separator="," />
          </el-col>
          <el-col :span="6">
            <el-statistic title="粉丝" :value="follower" :formatter="myformatter" />
          </el-col>
        </el-row>
        <el-row>
          <p class="demo-rich-content__desc" style="margin: 0; padding-left: 5%">
            反正火车总得创死一个，那就创死你吧。
          </p>
        </el-row>
        <el-divider />
        <el-row class="uservideo" style="height: 50%"> </el-row>
        <el-row>
          <el-pagination
            small
            background
            layout="prev, pager, next"
            :total="totalVideoPage"
            :page-size="9"
            class="mt-4"
          />
        </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<script setup>
import router from '../router'
let nickname = 'Eric'
let follow = 100213
let follower = 20004
function myformatter(val) {
  if (val > 10000) {
    return parseFloat(follower / 10000).toFixed(2) + '万'
  } else {
    return val + ''
  }
}

function gotoSetting() {
  router.push({ name: 'setting' })
}

let totalVideoPage = 50
</script>
<style scoped>
.userPage {
  height: 100%;
  width: 30%;
  margin-left: 35%;
  background-image: url('../public/userBackground.jpg');
  /* border-radius: 5%; */
  padding: 0;
}

.el-container {
  height: 100%;
  width: 100%;
  padding: 0;
  margin: 0;
}

.userinfo {
  height: 100%;
  width: 100%;
  padding: 0%;
  margin: 0;
  background-color: aliceblue;
  border-radius: 5%;
}

.usertop {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 20%;
}

.useravatar {
  padding: 0;
  margin: 0;
  height: 15vh;
  width: 15vh;
  position: absolute;
  top: 12%;
  left: 2%;
  z-index: 999;
  border-radius: 100%;
  overflow: hidden;
  border: solid 3px;
  border-color: aliceblue;
}

.el-avatar {
  height: 15vh;
  width: 15vh;
}
.nickname {
  padding-top: 7vh;
  padding-left: 6vh;
  font-size: 26px;
  font-weight: 500;
}
.el-pagination {
  margin: auto;
}
</style>
