<script setup>
import TheHeader from './components/TheHeader.vue'
import TheNav from './components/TheNav.vue';
import TheActivities from './pages/TheActivities.vue'; 
import TheProgress from './pages/TheProgress.vue';
import TheTimeline from './pages/TheTimeline.vue'

import {PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS} from '@/constants.js'
import {ref} from "vue"


const currentPage = ref(normalizePageHash())

function normalizePageHash() {
  const hash = window.location.hash.slice(1);

  if([PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS].includes(hash)){
    return hash;
  }
  window.location.hash = PAGE_TIMELINE

  return PAGE_TIMELINE

}
</script>

<template>
  <TheHeader/>

  <main class="flex flex-grow flex-col">
    <TheTimeline v-show="currentPage == PAGE_TIMELINE"/>
    <TheProgress v-show="currentPage == PAGE_PROGRESS"/>
    <TheActivities v-show="currentPage == PAGE_ACTIVITIES"/>
  </main>

  <TheNav :current-page="currentPage" @navigate="currentPage = $event"/>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
