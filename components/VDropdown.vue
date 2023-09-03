<template>
  <div class="relative inline-block">
    <VButton :title="title" :icon="icon" @handleClick="toggleDropdown" />
    <div v-if="isOpen" class="absolute top-10 z-10 left-0 mt-2 w-[204px] bg-white border rounded-lg text-black">
      <slot  @click="handleClick"></slot>
    </div>
  </div>
</template>

<script setup>
import { ref  } from 'vue';
defineProps(['title', 'icon'])


const isOpen = ref(false);
const { emit } = defineEmits();

const toggleDropdown = () => {
  isOpen.value = !isOpen.value;
};

const handleClick = (item) => {
  emit('handleClick', item);
  closeDropdown(); 
};

const closeDropdown = () => {
  isOpen.value = false;
};
</script>

<style scoped>
</style>
