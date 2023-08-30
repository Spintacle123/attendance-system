<template>
       <button @click="$emit('handleClick')" :class="[styled ? 'secondary' : 'primary', 'flex items-center gap-4 py-3 px-6 rounded-lg']">
        <Icon :icon="icon" /> {{ title }}
      </button>
</template>
<script setup>
import { Icon } from '@iconify/vue';
defineProps(['title', 'styled', 'icon', 'on-click'])
defineEmits(['handleClick'])
</script>
<style>
.primary{
    background-color: #E42323;
    color:white;
}
.secondary{
    background-color: #fff;
    color:#000;
    border:1px solid #E6E6E6;
}
</style>