<template>
    <header class="fixed top-0 flex justify-between items-center py-4 px-8 bg-white border-b-2 border-custom-gray w-[100vw] z-30">
      <img src="/img/logo.png" class="w-[178px]">
      <Icon @click="isOpen = !isOpen" icon="ic:baseline-menu" :style="{ fontSize: '24px', color: '#a3a3a3', cursor: 'pointer' }"/>
    </header>
   <!-- dropdown --> 
    <div v-if="isOpen" id="dropdown" class="fixed right-8 top-16 w-[204px]  bg-white border rounded-lg z-30">
      <ul class="flex flex-col h-[100%] text-[12px] font-bold cursor-pointer">
        <li @click="addAdmin= !addAdmin"  class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="ic:outline-plus" /> Create Admin Account</li>
        <li @click="updateAdmin= !updateAdmin" class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="material-symbols:update" /> Update Admin Account</li>
        <li class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="iconamoon:settings" /> Settings</li>
        <li @click="navigateTo('/login')" class="flex grow gap-2 items-center p-4 hover:bg-red-100"><Icon icon="material-symbols:logout" /> Log Out</li>
      </ul>
    </div>
    <AdminForm v-if="addAdmin" @close-modal="addAdmin= false" title="Register to create your admin account" @handle-click="addAdmin=false"/>
    <AdminForm v-if="updateAdmin" @close-modal="updateAdmin= false" title="Update admin account" />
  </template>


<script setup>

    import { Icon } from '@iconify/vue';
    import { ref  } from 'vue'
    const isOpen=ref(false)
    const addAdmin=ref(false)
    const updateAdmin=ref(false)



</script>