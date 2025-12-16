<script setup>
  import NavBar from './components/NavBar.vue';
  import LoginHomeP from './components/LoginHomeP.vue';
</script>

<template>
<NavBar/>
<div class="page-content">
    <LoginHomeP/>
  </div>
</template>

<style scoped>
.page-content {
  /* Mivel a navbar 60px magas, adjunk neki 80px helyet fentről */
  padding-top: 80px; 
}
</style>
