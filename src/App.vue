<script setup>
import UserCardView from './components/UserCardView.vue'
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-header direction="horizontal"><UserCardView></UserCardView></el-header>
      <el-main>
        <RouterView />
      </el-main>
    </el-container>
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
</style>
