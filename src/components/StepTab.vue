<template>
  <div class="step-tab" :class="{ active }" @click="$emit('click')">
    <div v-if="src" class="icon">
      <img :src="src" alt="" srcset="" />
    </div>
    <input v-else type="radio" :checked="active" />
    <p>{{ text }}</p>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  text: string
  active?: boolean
  src?: string
}>()
</script>

<style lang="scss" scoped>
.step-tab {
  padding-left: 20px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  gap: 10px;
  box-shadow: rgba(138, 138, 153, 0.2) 0px 5px 10px 0px;
  cursor: pointer;
  height: 90px;
  width: 230px;

  .icon {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: #e3e0ff;
    display: flex;
    justify-content: center;
    align-items: center;

    img {
      width: 50%;
      height: 50%;
    }
  }

  p {
    font-weight: 600;
  }
}

.active {
  border: 2px solid #4a3aff;
}
</style>
