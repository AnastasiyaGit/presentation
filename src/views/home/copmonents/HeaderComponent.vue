<template>
<div id="header">
<img src="/logo.svg" height="50px" width="auto" class="logo" @click="reloadFunc">
</div>
</template>

<script setup>
const reloadFunc = ()=>{
  location.reload()
}
</script>

<style scoped lang="scss">
#header{
  display: flex;
  align-items: center;
  background-color: #3e434a;
  height: 60px;
  width: 100%;
  overflow: hidden;
  //white-space: nowrap;
  //box-sizing: border-box;
  .logo{
    transform: translateX(-200%);
    padding-left: 100%;
    animation: marquee 10s linear infinite;
  }
}
@keyframes marquee {
  from { transform: translateX(0%); }
  to { transform: translateX(-100%); }
}
</style>
