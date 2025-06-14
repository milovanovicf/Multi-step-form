<template>
  <div>
    <label v-if="label" :for="label"
      ><span v-if="label === 'Name' || label === 'Email'" class="required">* </span>{{ label }}
    </label>
    <div class="input">
      <input
        :type="type"
        :name="label"
        :id="label"
        :placeholder="placeholder"
        :style="{ width: width }"
        :value="props.modelValue"
        @input="(e) => emit('update:modelValue', (e.target as HTMLInputElement)?.value || '')"
        autocomplete="off"
      />
      <ActionButton v-if="showButton" buttonText="Subscibe" paddings="8px 20px" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineEmits, defineProps } from 'vue'
import ActionButton from './ActionButton.vue'

const emit = defineEmits(['update:modelValue'])

const props = defineProps<{
  width?: string
  placeholder: string
  showButton: boolean
  label?: string
  modelValue?: string
  type?: string
}>()
</script>

<style scoped lang="scss">
.input {
  background-color: #fff;
  display: flex;
  border-radius: 35px;
  border: 1px solid #eeeeee;
  align-items: center;
  justify-content: space-between;
  padding: 8px 10px;
  box-shadow: rgba(138, 138, 153, 0.2) 0px 7px 29px 0px;

  input {
    border: none;
    margin-left: 20px;
    padding: 10px 0 10px 0;
    font-family: 'Montserrat', sans-serif;

    &:focus {
      outline: none;
    }
  }

  ::placeholder {
    color: rgb(145, 145, 145);
  }
}

label {
  display: block;
  margin-bottom: 15px;
  font-weight: 500;
}

.required {
  color: #a01c1c;
}
</style>
