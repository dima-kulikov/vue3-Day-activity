<script setup>
import NavItem from './NavItem.vue';
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import {PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS} from '@/constants.js'

defineProps(['currentPage'])
const emit = defineEmits(['navigate'])

const navItem = {
  [PAGE_TIMELINE]: ClockIcon,
  [PAGE_ACTIVITIES]: ListBulletIcon,
  [PAGE_PROGRESS]: ChartBarIcon
}
</script>

<template>
    <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="atems-center flex justify-around border-t">
      <NavItem  v-for="(value, key) in navItem" :key="key" :href="`#${key}`" :class="{'bg-gray-200 pointer-events-none' : key == currentPage}"
      @click="emit('navigate', key)"
      >
        <component :is="value" class="w-6 h-6"/>{{ key }}
      </NavItem>
    </ul>
  </nav>
</template>