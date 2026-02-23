<template>
    <div class="absolute w-full max-w-md bg-secondary shadow-inner rounded-xl animate-open-window max-h-96 h-full overflow-hidden font-secondary"
        :class="{ 'bg-secondary-dark': isDark, 'text-white': isDark }">
        <div class="flex flex-col items-start p-5 w-full">
                <b>Results</b>
                <p class="text-sm sm:text-base">{{ results }}</p>
                <b class="mt-4">Reasoning</b>
                <p class="text-sm sm:text-base">{{ reasoning }}</p>
         </div>
    </div>
    
</template>

<script setup>
import { ref, computed } from "vue"
const colorMode = useColorMode()

const isDark = computed({
  get() {
    return colorMode.value === 'dark'
  },
  set(_isDark) {
    colorMode.preference = _isDark ? 'dark' : 'light'
  }
})


const results = ref("This patient is at risk for Alzheimer's Disease")
const reasoning = ref("Abnormally large alpha waves");

</script>