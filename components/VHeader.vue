<template>
    <header class="fixed top-0 flex justify-between items-center py-4 px-8 bg-white border-b-2 border-custom-gray w-[100vw]">
      <img src="/img/logo.png" class="w-[178px]">
      <Icon @click="isOpen = !isOpen" icon="ic:baseline-menu" :style="{ fontSize: '24px', color: '#a3a3a3', cursor: 'pointer' }"/>
    </header>
   <!-- dropdown --> 
    <div v-if="isOpen" id="dropdown" class="absolute right-8 top-16 w-[204px] h-[160px] bg-white border rounded-lg">
      <ul class="flex flex-col h-[100%] text-[12px] font-bold">
        <li class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="ic:outline-plus" /> Create Admin Account</li>
        <li class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="material-symbols:update" /> Update Admin Account</li>
        <li class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="material-symbols:logout" /> Log Out</li>
      </ul>
    </div>
  </template>


<script setup>
    import { Icon } from '@iconify/vue';
    import { ref  } from 'vue'
    const isOpen=ref(false)
</script>