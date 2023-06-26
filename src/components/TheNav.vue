<script setup>

import NavItem from './NavItem.vue';

import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
const navItem = {
  timeLine: ClockIcon,
  activities: ListBulletIcon,
  progress: ChartBarIcon
}

const currentPage = 'timeline'
</script>

<template>
    <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="atems-center flex justify-around border-t">
      <NavItem  v-for="(value, key) in navItem" :key="key" :href="`#${key}`" :class="{'bg-gray-200' : currentPage === 'timeline'}">
        <component :is="value" class="w-6 h-6"/>{{ key }}
      </NavItem>
    </ul>
  </nav>
</template>