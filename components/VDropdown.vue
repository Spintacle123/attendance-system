<template>
<!-- dropdown --> 
<div class="relative inline-block">
    <VButton :title="title" :icon="icon" @handleClick="isOpen = !isOpen" />
    <div  v-if="isOpen" class="absolute top-10 z-30 left-0 mt-2 w-[204px] bg-white border rounded-lg text-black">
      <ul  v-for="item in list" class="flex flex-col text-[12px] font-bold">
        <li @click="$emit('handleClick')" class="flex items-center gap-4 p-4 hover:bg-red-100 cursor-pointer"><Icon :icon="item.icon" /> {{ item.title }}</li>
      </ul>
    </div>
  </div>
</template>

<script setup>

    import { Icon } from '@iconify/vue';
    import { ref  } from 'vue'

    defineProps(['title', 'styled', 'icon','iconBtn', 'on-click', 'list'])
    defineEmits(['handleClick'])

    const isOpen=ref(false)
</script>