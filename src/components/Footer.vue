<template>
  <div class="footer">
    <div class="left-side">
      <div class="logo">
        <img src="../assets/Logo.png" alt="" />
      </div>
      <p class="copyright">Copyright © 2021 BRIX Templates | All Rights Reserved</p>
    </div>
    <div class="right-side">
      <Input width="300px" placeholder="Enter your email" show-button />
    </div>
  </div>
</template>

<script setup lang="ts">
import Input from './Input.vue'
</script>

<style scoped>
.footer {
  display: flex;
  justify-content: space-between;
  border-top: 1px solid #eeeeee;
  padding-top: 35px;
  width: 100%;

  .logo {
    width: 200px;

    img {
      width: 100%;
    }
  }
}
</style>
