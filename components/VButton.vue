<template>
       <button @click="$emit('handleClick')" :class="[iconBtn? 'iconOnly': styled  ? styled : 'primary', 'flex items-center gap-4 py-3 px-6 rounded-lg']">
        <Icon v-if="icon" :icon="icon" :class="iconBtn"/> {{ title }}
      </button>
</template>
<script setup>
import { Icon } from '@iconify/vue';
defineProps(['title', 'styled', 'icon','iconBtn', 'on-click'])
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
.secondarySmallBtn{
    background-color: #fff;
    color:#000;
    font-size: 14px;
    border:1px solid #E6E6E6;
    padding:0.5em !important;
}
.iconOnly{
    background-color:transparent;
}
.iconBtn{
    color:#E42323;
}
</style>