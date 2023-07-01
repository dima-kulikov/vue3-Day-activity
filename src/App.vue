<script setup>
import TheHeader from './components/TheHeader.vue'
import TheNav from './components/TheNav.vue';
import TheActivities from './pages/TheActivities.vue'; 
import TheProgress from './pages/TheProgress.vue';
import TheTimeline from './pages/TheTimeline.vue'
import {normalizePageHash} from './functions.js'
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from './constants'

import {ref} from "vue"


const currentPage = ref(normalizePageHash())


function goTo(page){
  currentPage.value = page
}
</script>

<template>
  <TheHeader 
  @go-to-time-line="goTo(PAGE_TIMELINE)"
  @go-to-progress="goTo(PAGE_PROGRESS)"
  />

  <main class="flex flex-grow flex-col">
    <TheTimeline v-show="currentPage == PAGE_TIMELINE"/>
    <TheProgress v-show="currentPage == PAGE_PROGRESS"/>
    <TheActivities v-show="currentPage == PAGE_ACTIVITIES"/>
  </main>

  <TheNav :current-page="currentPage" @navigate="goTo($event)"/>
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
<!-- https://www.youtube.com/watch?v=GRAAjpeZKWE&list=PL-FhWbGlJPfaCm9Qx7G9wQqtt2_yBT92V&index=13
ПАУЗА НА 13 ВИДЕО, ИХ МНОГО, БОЛЬШОЙ ПРОЕКТ
-->