<template>
  <div class="steps-container">
    <div v-if="currentStep < 5" class="steps">
      <ul>
        <li :class="{ active: currentStep === 1 }">1</li>
        <li :class="{ active: currentStep === 2 }">2</li>
        <li :class="{ active: currentStep === 3 }">3</li>
        <li :class="{ active: currentStep === 4 }">4</li>
      </ul>
    </div>
    <div class="content">
      <StepContent
        v-if="currentStep === 1"
        title="Contact details"
        subtext="Lorem ipsum dolor sit amet consectetur adipisc."
      >
        <Input :showButton="false" label="Name" placeholder="John Carter" v-model="formData.name" />
        <Input
          :showButton="false"
          label="Email"
          placeholder="Email address"
          v-model="formData.email"
          type="email"
        />
        <Input
          :showButton="false"
          label="Phone Number"
          placeholder="(123) 456 - 7890"
          v-model="formData.phone"
          type="tel"
        />
        <Input
          :showButton="false"
          label="Company"
          placeholder="Company name"
          v-model="formData.company"
        />
      </StepContent>

      <StepContent
        v-if="currentStep === 2"
        title="Our services"
        subtext="Please select which services you are interested in."
      >
        <StepTab
          text="Development"
          :src="codeIcon"
          :active="formData.service === 'development'"
          @click="formData.service = 'development'"
        />
        <StepTab
          text="Web Design"
          :src="tabsIcon"
          :active="formData.service === 'web-design'"
          @click="formData.service = 'web-design'"
        />
        <StepTab
          text="Marketing"
          :src="megaphoneIcon"
          :active="formData.service === 'marketing'"
          @click="formData.service = 'marketing'"
        />
        <StepTab
          text="Other"
          :src="gearIcon"
          :active="formData.service === 'other'"
          @click="formData.service = 'other'"
        />
      </StepContent>

      <StepContent
        v-if="currentStep === 3"
        title="What’s your project budget?"
        subtext="Please select the project budget range you have in mind."
      >
        <StepTab
          text="$5.000 - $10.000"
          :active="formData.budget === '5k-10k'"
          @click="formData.budget = '5k-10k'"
        />
        <StepTab
          text="$10.000 - $20.000"
          :active="formData.budget === '10k-20k'"
          @click="formData.budget = '10k-20k'"
        />
        <StepTab
          text="$20.000 - $50.000"
          :active="formData.budget === '20k-50k'"
          @click="formData.budget = '20k-50k'"
        />
        <StepTab
          text="$50.000 +"
          :active="formData!.budget === '50k+'"
          @click="formData.budget = '50k+'"
        />
      </StepContent>

      <StepContent
        v-if="currentStep === 4"
        title="Submit your quote request"
        subtext="Please review all the information you previously typed in the past steps, and if all is okay, submit your message to receive a project quote in 24 - 48 hours."
        last
        @submit="$emit('submit')"
      />

      <StepContent
        v-if="currentStep === 5"
        title="Thank You for Your Request!"
        subtext="We’ve received your project details and will get back to you with a personalized quote within 24-48 hours. If you have any questions in the meantime, feel free to reach out."
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { inject, computed } from 'vue'
import StepContent from './StepContent.vue'
import Input from './Input.vue'
import StepTab from './StepTab.vue'
import codeIcon from '../assets/code.png'
import tabsIcon from '../assets/tabs.png'
import megaphoneIcon from '../assets/megaphone.png'
import gearIcon from '../assets/gear.png'

const props = defineProps<{
  currentStep: number
}>()

const step = computed(() => props.currentStep)

type FormData = {
  name: string
  email: string
  phone: string
  company: string
  service: string
  budget: string
}

const formData = inject<FormData>('formData', {
  name: '',
  email: '',
  phone: '',
  company: '',
  service: '',
  budget: '',
})
</script>

<style lang="scss">
.steps-container {
  display: flex;
  flex-direction: column;
  border-radius: 25px;
  border: 1px solid #eeeeee;
  box-shadow: rgba(138, 138, 153, 0.2) 0px 7px 29px 0px;
  width: 50%;
  height: 500px;
  margin: 20px auto;
  padding: 20px 40px;

  .steps {
    ul {
      display: flex;
      justify-content: space-around;
      width: 100%;
      border-bottom: 1px solid #eeeeee;
      padding-bottom: 15px;

      li {
        display: flex;
        justify-content: center;
        align-items: center;
        list-style: none;
        background-color: #ececec;
        color: #919191;
        border-radius: 50%;
        width: 30px;
        height: 30px;
      }

      .active {
        background-color: #4a3aff;
        color: #fff;
      }
    }
  }

  .content {
    text-align: left;
  }
}
</style>
