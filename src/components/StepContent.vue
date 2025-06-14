<template>
  <div class="step-content" :class="{ last }">
    <div v-if="last" class="image-container">
      <img src="../assets/check.png" alt="" srcset="" class="image-success" />
    </div>
    <div class="text">
      <h3 :class="{ last }">{{ title }}</h3>
      <p :class="{ last }">{{ subtext }}</p>
    </div>
    <div v-if="!last" class="content">
      <slot></slot>
    </div>
    <ActionButton v-if="last" button-text="Subscribe" @click="$emit('submit')" />
  </div>
</template>

<script setup lang="ts">
import ActionButton from './ActionButton.vue'
import { inject } from 'vue'

withDefaults(
  defineProps<{
    title: string
    subtext: string
    last?: boolean
    active?: boolean
  }>(),
  {
    last: false,
    active: false,
  },
)
const formData = inject('formData')
</script>

<style lang="scss" scoped>
.step-content {
  padding-bottom: 50px;

  .image-container {
    width: 120px;
    height: 110px;
    margin-top: 30px;

    img {
      width: 100%;
      height: 100%;
    }
  }

  .text {
    margin: 60px 0 20px 0;

    h3 {
      font-weight: 600;
      font-size: 22px;
    }
  }

  .content {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 1fr);
    gap: 20px;
    width: 100%;
    margin: auto;
  }
}

.last {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
