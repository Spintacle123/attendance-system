<template>
    <main class="flex flex-col items-center gap-4 py-6 px-8 mt-2 bg-white">
      <div class="flex items-center grow gap-6 p-4 rounded-lg border-2 border-custom-gray w-[100%]">
        <div class="flex items-center gap-4 p-4 w-[40%]">
            <Icon icon="mdi:megaphone" :style="{ fontSize: '64px', color: '#E42323' }"/>
            <span class="font-bold text-2xl text-[#000]">Today, 23 August 2023</span>
        </div>
        <VCard title="Total Employees"/>
        <VCard title="On Time"/>
        <VCard title="Late In"/>
        <VCard title="Absent"/>
      </div>  
    </main>
</template>
<script setup>
import { Icon } from '@iconify/vue';
</script>