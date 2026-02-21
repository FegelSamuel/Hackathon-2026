<template> 
    <button class="py-1 px-4 m-2 bg-primary hover:bg-primary-hover rounded-full font-secondary text-white transition text-center shadow-lg"> 
        {{ text }}
    </button>
</template>

<script setup>
const props = defineProps(['text'])
</script>