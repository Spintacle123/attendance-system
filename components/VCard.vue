<template>
    <div class="flex flex-col border-2 rounded-xl px-6 py-3 w-[14%] font-bold">
        <h2 class="text-[#808080] text-[15px]">{{ title }}</h2>
        <span class="text-[24px]">{{ total }}</span>
        <div class="flex justify-end ">
            <div class="p-2 rounded-full" :style="{backgroundColor:color? color:  '#2E8F00'  }">
                <Icon :icon="icon" :style="{ fontSize: '24px', color: '#fff', cursor: 'pointer' }" />
            </div>        
        </div>
    </div>
</template>
<script setup>
import { Icon } from '@iconify/vue';
defineProps(['title', 'total', 'color', 'icon'])
</script>