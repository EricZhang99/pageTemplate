<script setup>
// showCard = false;
showCard = false;
function log() {
    console.log("click")
    showCard = !showCard
}
</script>

<template>
    <div class="block" @click=log>
        <el-avatar :size="50" :src="circleUrl" />
    </div>
    <div v-show=showCard class="userCard">
        hello
    </div>
</template>

<style scoped>
.userCard {
    height: 20vh;
    width: 20VH;
    position: relative;
    color: blue;
}
</style>