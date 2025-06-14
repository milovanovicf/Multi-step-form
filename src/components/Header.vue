<template>
  <div class="header">
    <div class="logo"><img src="../assets/Logo.png" /></div>
    <ActionButton buttonText="Clone now" paddings="10px 25px" />
  </div>
</template>

<script setup lang="ts">
import ActionButton from './ActionButton.vue'
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  width: 100%;

  .logo {
    width: 250px;

    img {
      width: 100%;
    }
  }
}
</style>
