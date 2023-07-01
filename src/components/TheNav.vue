<script setup>
import NavItem from './NavItem.vue';
import {NAV_ITEMS} from '../constants'

defineProps(['currentPage'])
const emit = defineEmits(['navigate'])


</script>

<template>
    <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="atems-center flex justify-around border-t">
      <NavItem  v-for="(value, key) in NAV_ITEMS" :key="key" :href="`#${key}`" :class="{'bg-gray-200 pointer-events-none' : key == currentPage}"
      @click="emit('navigate', key)"
      >
        <component :is="value" class="w-6 h-6"/>{{ key }}
      </NavItem>
    </ul>
  </nav>
</template>