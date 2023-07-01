<script setup>

import TheLogo from './TheLogo.vue';
import TheHeaderProgre from './TheHeaderProgress.vue'

const emit = defineEmits(['goToTimeLine', 'goToProgress'])
</script>


<template>
    <header class="sticky top-0 z-20 flex items-center justify-between border-b bg-white p-3">
   <TheLogo v-on:click="emit('goToTimeLine')"/>
    <TheHeaderProgre v-on:click="emit('goToProgress')"/>
  </header>
</template>