<template>
  <div class="container">
    <Header />
    <h1 v-if="currentStep < 5">Get a project quote</h1>
    <p v-if="currentStep < 5">
      Please fill the form below to receive a quote for your project. Feel free to add as much
      detail as needed.
    </p>
    <Transition name="fade" mode="out-in">
      <StepContainer :current-step="currentStep" :key="currentStep" @submit="handleSubmit" />
    </Transition>
    <div v-if="currentStep < 5" class="buttons">
      <ActionButton
        buttonText="Previous step"
        ghost
        @click="prev"
        v-if="currentStep > 1 && currentStep < 5"
        id="prev"
      />
      <ActionButton
        buttonText="Next step"
        @click="next"
        v-if="currentStep < 4"
        id="next"
        :disabled="!formData.name || !formData.email"
      />
    </div>
    <Footer />
  </div>
</template>

<script setup lang="ts">
import { ref, reactive, provide } from 'vue'

import Header from './Header.vue'
import Footer from './Footer.vue'
import StepContainer from './StepContainer.vue'
import ActionButton from './ActionButton.vue'

const currentStep = ref(1)

const next = () => {
  if (currentStep.value < 4) currentStep.value++
}
const prev = () => {
  if (currentStep.value > 1) currentStep.value--
}

function handleSubmit() {
  console.log('triggers')

  currentStep.value = 5
}

const formData = reactive({
  name: null,
  email: null,
  phone: null,
  company: null,
  service: 'development',
  budget: '5k-10k',
})

provide('formData', formData)
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease-in-out;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.container {
  background-color: #fff;
  padding: 40px 50px;
  width: 1280px;
  border-radius: 40px;
  margin: 0 auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;

  h1,
  p {
    width: 40%;
  }

  h1 {
    font-weight: 800;
  }

  p {
    margin-bottom: 20px;
  }

  .buttons {
    /* display: flex;
    justify-content: space-between; */
    width: 50%;
    margin-bottom: 100px;
    position: relative;

    #prev {
      position: absolute;
      left: 0;
    }

    #next {
      position: absolute;
      right: 0;
    }
  }
}
</style>
