<template>
  <button class="button" :style="{ padding: paddings }" :class="{ ghost }">
    {{ buttonText }}
  </button>
</template>

<script setup lang="ts">
defineProps<{
  buttonText: string
  paddings?: string
  ghost?: boolean
}>()
</script>

<style scoped>
.button {
  display: block;
  background-color: #4a3aff;
  color: #fff;
  padding: 14px 35px;
  border-radius: 50px;
  width: max-content;
  transition: all 200ms ease-in-out;
  cursor: pointer;
  border: none;

  &:hover {
    background-color: #382bc4;
  }

  &:disabled {
    cursor: not-allowed;
    opacity: 0.6;
  }
}

.ghost {
  background-color: #fff;
  color: #4a3aff;
  border: 1px solid #4a3aff;

  &:hover {
    background-color: #dbdada;
  }
}
</style>
