<template>
    <div class="flex items-center justify-center fixed inset-0 w-screen h-screen bg-[#a2a2a28e] z-40">
      <div class="flex flex-col justify-between gap-3 absolute top-[50%] left-[50%] transform translate-x-[-50%] translate-y-[-50%] px-12 py-6 rounded-lg bg-white shadow-md  text-center w-[50%] min-h-[70%]" :style="{ borderColor: color}">
        <header class="flex gap-4 items-center border-b border-gray-100 py-5">
          <img src="img/logo-small.png" class=" object-cover w-[67px] h-[67px]"/>
          <div class="flex flex-col text-left">
            <h2 class="text-sm font-bold">Welcome to Intelliseven</h2>
            <span class="text-gray-500 ">{{title}}</span>
          </div>
        </header>
        <div class="flex gap-8">
          <label for="img" class="w-[20%]">
            <img class="w-[50px] rounded-full border border-gray-100 "  src="https://static.vecteezy.com/system/resources/previews/008/506/404/original/contact-person-red-icon-free-png.png" alt="upload image"/>
            <input type="file" id="img" class="hidden"/>
          </label>
          <div class="flex flex-wrap gap-8 w-[100%]">
            <div class="grow flex flex-col gap-2">
              <VInput title="First Name" required="true" type="text" v-model="fName"/>
              <VInput title="Email" required="true" type="email" v-model="email"/>
              <VInput title="Job Position" required="true" type="text" v-model="position"/>
              <VInput title="Password" required="true" type="password" v-model="password"/>
            </div>
            <div class="grow flex flex-col gap-2">
              <VInput title="Last Name" required="true" type="text" v-model="lName"/>
              <VInput title="Contact Number" required="true" type="text" v-model="number"/>
              <VInput title="Shift" required="true" type="text" v-model="shift"/>
              <VInput title="ID Number" :placeholder="autoID" required="true" type="text" readonly="true" v-model="autoID" />
              
            
            </div>
          </div>
        </div>
        <div class="flex  justify-start gap-2 py-4">
          <input type="checkbox"/> I agree to the privacy notice and data processing agreement
        </div>
        <div class="flex gap-8 p-2  w-[100%] items-end justify-end">
          <div class="flex gap-4">
            <button class="grow w-[91px] h-[46px] rounded-lg text-[12px] text-[#909090] bg-[#D9D9D9]" @click="closeModal">Cancel</button>
            <button class="grow w-[91px] h-[46px] rounded-lg text-[12px] text-white bg-custom-red"  @click="handleClick">Create Account</button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
<script setup>
    import { ref, defineEmits } from 'vue';
    const autoID = ref(generateAutoID());
    
    const fName = ref('')
    const lName = ref('')
    const email = ref('')
    
    const position = ref('')
    const shift = ref('')
    const number = ref('')
    defineProps(['title','subtitle', 'img','color','name','secondBtn','verification'])
    const emit = defineEmits();
    const closeModal = () => {
        emit('close-modal');
    };
    const handleClick = () => {
        
        console.log(autoID.value)
        console.log(fName.value," ",lName.value)
        console.log(email.value)
        console.log(number.value)
        console.log(position.value)

        emit('handle-click');
       
    };

    function generateAutoID() {
    const timestamp = new Date().getTime(); // Get the current timestamp
    const randomNum = Math.floor(Math.random() * 10000); 

    return `${timestamp}${randomNum}`;
  }



</script>