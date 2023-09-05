<template>
    <div class="flex flex-col gap-1 w-[100%]">
      <label class="text-left font-bold text-xs">{{ title }} <span v-if="required" class=" text-red-400">*</span></label>
      
      <input
        :id="title"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :type="type"
        :readonly="readonly"
        :placeholder="placeholder"
        class="grow p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-[10px] h-[37px] border border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400 relative"
      />
      
    </div>
  </template>
<script setup>
  defineProps(['title', 'readonly', 'required', 'type','modelValue'])
  defineEmits(['update:modelValue'])


</script>