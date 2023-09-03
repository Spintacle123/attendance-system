<template>
    <div class="flex items-center justify-center fixed inset-0 w-screen h-screen bg-[#d9d9d966] z-40">
      <div class="flex flex-col items-center gap-3 absolute top-[50%] left-[50%] transform translate-x-[-50%] translate-y-[-50%] px-4 py-8 rounded-lg bg-white shadow-md  text-center" :style="{ borderColor: color}">
        <img 
          v-if="img" 
          src="data:image/png;base64,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" alt="" 
          class="object-cover w-[60px] h-[60px] rounded-full" />
        <h4 class="font-bold mb-4">{{ title }}</h4>
        <p class="w-[386px] text-xs">{{ subtitle }}</p>
<!-- this will only show for the verification/login modal -->        
        <div v-if="verification">
          <form action="" method="post">
          <div class="flex flex-col ">
            <div class="flex flex-row items-center justify-between gap-2 mx-auto w-full max-w-xs">
              <div class="w-16 h-16 ">
                <input class="w-full h-full flex flex-col items-center justify-center text-center px-5 outline-none rounded-xl border border-gray-200 text-lg bg-white focus:bg-gray-50 " type="text" name="" id="" maxlength="1">
              </div>
              <div class="w-16 h-16 ">
                <input class="w-full h-full flex flex-col items-center justify-center text-center px-5 outline-none rounded-xl border border-gray-200 text-lg bg-white focus:bg-gray-50 " type="text" name="" id="" maxlength="1">
              </div>
              <div class="w-16 h-16 ">
                <input class="w-full h-full flex flex-col items-center justify-center text-center px-5 outline-none rounded-xl border border-gray-200 text-lg bg-white focus:bg-gray-50 " type="text" name="" id="" maxlength="1">
              </div>
              <div class="w-16 h-16 ">
                <input class="w-full h-full flex flex-col items-center justify-center text-center px-5 outline-none rounded-xl border border-gray-200 text-lg bg-white focus:bg-gray-50 " type="text" name="" id="" maxlength="1">
              </div>
            </div>
          </div>
        </form>
        </div>
        <div class="flex gap-8 p-2 justify-center w-[80%]">
          <button v-if="secondBtn" class="grow w-[91px] h-[46px] rounded-lg text-[12px] text-[#909090] bg-[#D9D9D9]" @click="closeModal">{{ secondBtn }}</button>
          <button class="grow w-[91px] h-[46px] rounded-lg text-[12px] text-white" :style="{ backgroundColor: color}" @click="handleClick">{{ name }}</button>
        </div>
      </div>
    </div>
  </template>
  
<script setup>
    import { ref, defineEmits } from 'vue';
    
    defineProps(['title','subtitle', 'img','color','name','secondBtn','verification'])
    const emit = defineEmits();
    const closeModal = () => {
        emit('close-modal');
    };
    const handleClick = () => {
        emit('handle-click');
    };
</script>