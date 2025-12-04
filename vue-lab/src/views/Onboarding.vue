<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const currentStep = ref(0)

const steps = [
  {
    image: 'https://elements-resized.envatousercontent.com/elements-cover-images/17170584-6276-4884-a568-c81f88a63ed1?w=2038&cf_fit=scale-down&q=85&format=auto&s=e203ea40c647f93037f7731ccd4c70987a317c0ff6e612eb9f8dc23baf9ee64c',
    title: 'MEET NEW PEOPLE',
    text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur malesuada libero ex, at vestibulum mauris consequat ut.'
  },
  {
    image: 'https://elements-resized.envatousercontent.com/elements-cover-images/bdfffbdc-fce8-472a-9250-b26f570ece3a?w=2038&cf_fit=scale-down&q=85&format=auto&s=b13c249aff40662e789f2f6a017189952fb44f55e39c0f9834845c936cb351fd',
    title: 'CHAT WITH EASE',
    text: 'Proin sodales massa a purus scelerisque, vel ultricies leo blandit. Sed urna libero, lacinia sit amet dictum eu.'
  },
  {
    image: 'https://elements-resized.envatousercontent.com/elements-cover-images/e0510cdc-12f5-4440-85dc-a6f9c09638a8?w=2038&cf_fit=scale-down&q=85&format=auto&s=329fee46edbc2aa676a026d306d147f87069160f6eebd2009451139b9a5eb685',
    title: 'FIND YOUR MATCH',
    text: 'Sed urna libero, lacinia sit amet dictum eu, elementum et metus. Curabitur malesuada libero ex.'
  }
]

const nextStep = () => {
  if (currentStep.value < steps.length - 1) {
    currentStep.value++
  } else {
    finishOnboarding()
  }
}

const goToStep = (index: number) => {
  currentStep.value = index
}

// Функція переходу на Логін
const finishOnboarding = () => {
  router.push('/login')
}
</script>

<template>
  <div class="bg-gray-200 py-10 min-h-screen flex justify-center items-center">
    
    <section class="w-[375px] h-[812px] bg-white rounded-[30px] border-2 border-black 
                    flex flex-col justify-between p-6 overflow-hidden relative">

      <img
        :src="steps[currentStep].image"
        alt="onboarding screen"
        class="w-full mt-24 scale-[1.10] object-cover h-[300px]"
      />

      <div class="text-center z-10">
        <h2 
          @click="finishOnboarding"
          class="bg-[#ff6f6f] text-white text-[22px] font-bold rounded-md px-8 py-3 inline-block mb-5 cursor-pointer hover:bg-[#ff5555] transition select-none"
        >
          {{ steps[currentStep].title }}
        </h2>

        <p class="text-[12px] text-gray-700 leading-[1.35] w-[85%] mx-auto">
          {{ steps[currentStep].text }}
        </p>
      </div>

      <div class="flex items-center justify-between w-full">
        <button @click="finishOnboarding" class="px-6 py-3 bg-gray-200 rounded-md font-semibold hover:bg-gray-300 transition">
          SKIP
        </button>

        <div class="flex gap-2">
          <span 
            v-for="(step, index) in steps" 
            :key="index"
            @click="goToStep(index)"
            class="w-[10px] h-[10px] rounded transition-all duration-300 cursor-pointer hover:scale-125"
            :class="index === currentStep ? 'bg-[#ff6f6f]' : 'bg-[#ccc]'"
          ></span>
        </div>

        <button @click="nextStep" class="px-6 py-3 bg-[#ff6f6f] text-white rounded-md font-semibold hover:bg-[#ff5555] transition">
          NEXT
        </button>
      </div>

    </section>
  </div>
</template>