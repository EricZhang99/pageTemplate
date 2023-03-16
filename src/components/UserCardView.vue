<script setup>
// showCard = false;
var showCard = false
</script>

<template>
  <el-popover
    :width="300"
    popper-style="box-shadow: rgb(14 18 22 / 35%) 0px 10px 38px -10px, rgb(14 18 22 / 20%) 0px 10px 20px -15px; padding: 20px;"
    trigger="click"
  >
    <template #reference>
      <el-avatar
        src="https://picsum.photos/200"
        :size="100"
        style="max-height: 10vh; max-width: 10vh"
      />
    </template>

    <template #default>
      <div class="demo-rich-conent" style="display: flex; gap: 16px; flex-direction: column">
        <div class="userInfo" v-if="showCard">
          <el-avatar
            :size="60"
            src="https://picsum.photos/200"
            style="margin-bottom: 8px; margin-top: 8px"
          />
          <div>
            <p class="demo-rich-content__name" style="margin: 0; font-weight: 500">Element Plus</p>
            <p
              class="demo-rich-content__mention"
              style="margin: 0; font-size: 14px; color: var(--el-color-info)"
            >
              @element-plus
            </p>
          </div>

          <p class="demo-rich-content__desc" style="margin: 0">
            Element Plus, a Vue 3 based component library for developers, designers and product
            managers
          </p>
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
