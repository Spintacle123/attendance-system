<template>
    <div class="flex flex-col border-2 rounded-xl p-4 w-[14%] font-bold">
        <div>
            <h2 class="text-[#808080] text-[15px]">{{ title }}</h2>
            <span class="text-[24px]">50</span>
        </div>
        <div class="flex justify-end ">
            <div class="p-2 rounded-full bg-[#2E8F00] ">
                <Icon icon="clarity:employee-solid" :style="{ fontSize: '24px', color: '#fff', cursor: 'pointer' }" />
            </div>        
        </div>
    </div>
</template>
<script setup>
import { Icon } from '@iconify/vue';
defineProps(['title'])
</script>