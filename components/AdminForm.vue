<template>
    <div class="flex items-center justify-center fixed inset-0 w-screen h-screen bg-[#a2a2a28e] z-40">
      <div class="flex flex-col  gap-3 absolute top-[50%] left-[50%] transform translate-x-[-50%] translate-y-[-50%] px-4 py-6 rounded-lg bg-white shadow-md  text-center w-[60%] min-h-[70%]" :style="{ borderColor: color}">
        <header class="flex gap-4 items-center border-b border-gray-100 p-">
          <img src="img/logo-small.png" class=" object-cover w-[67px] h-[67px]"/>
          <div class="flex flex-col text-left">
            <h2 class="text-sm font-bold">Welcome to Intelliseven</h2>
            <span class="text-gray-500 ">Enter the details to register an employee</span>
          </div>
        </header>
        <div class="flex gap-8">
          <label for="img" class="w-[20%]">
            <img class="w-[50px] rounded-full border border-gray-100 "  src="https://static.vecteezy.com/system/resources/previews/008/506/404/original/contact-person-red-icon-free-png.png" alt="upload image"/>
            <input type="file" id="img" class="hidden"/>
          </label>
          <div class="flex grow wrap w-[100%] gap-8 " >
            <div class="flex flex-col w-[100%] ">
                <label> Email</label>
                <input type="email"  class="grow p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            <div class="flex flex-col w-[100%]">
                <label> ID Number</label>
                <input type="text"  class="grow p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            <div class="flex flex-col w-[100%]">
                <label> Password</label>
                <input type="password"  class="grow p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
          </div>
        </div>
        <div class="flex gap-8 p-2 justify-center w-[80%]">
          <button class="grow w-[91px] h-[46px] rounded-lg text-[12px] text-[#909090] bg-[#D9D9D9]" @click="closeModal">{{ secondBtn }}</button>
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