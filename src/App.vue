<script setup>
import UserCardView from './components/UserCardView.vue';
</script>


<template>
  <div class="common-layout">
    <el-container>
      <el-header direction="horizontal"><UserCardView></UserCardView></el-header>
      <el-main>Main</el-main>
    </el-container>
  </div>
</template>


<style scoped>
.common-layout {
  height: 100%;
  width: 100%;
}
.el-container {
  line-height: 1.5;
  max-height: 100vh;
}
</style>
