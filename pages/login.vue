<template>
    <div class="flex items-center justify-center bg-cover bg-[url('img/login-bg.jpg')]  w-screen min-h-screen">
        <div class="flex flex-col px-12 py-24 items-center justify-center gap-5 w-[90vw] rounded-lg bg-white h-[80vh] md:w-[40vw] lg:w-[30vw] " >
<!-- login form header-->
            <header class="flex flex-col items-center justify-center">
                <img src="../public/img/logo-small.png" class="w-20 " />
                <h2 class="text-[15px] font-semibold">Intelliseven</h2>
                <span class="text-sm text-[#808080]">Technology Solutions Inc.</span>
            </header>
            
            <h1 class="font-bold">Sign In</h1>
            <div class="flex flex-col gap-4 w-[100%]">
                <div class="flex flex-col w-[100%]">
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
            <div class=" w-[100%]">
                <button class="bg-custom-red grow text-white px-4 py-2 mt-4 rounded-lg w-[100%]" @click="verification=!verification">SIGN IN</button>
            </div>
            </div>
        </div>
        <VModal 
            v-if="verification"  
            @close-modal="verification = false"  @handle-click="handleVerification" 
            title="Verification Code" 
            subtitle="Please enter the verification code sent to your email or mobile" 
            color="#E42326" 
            verification="true"   
            name="Verify"
        />
    </div>
</template>

<script setup>
import { ref  } from 'vue'

const verification=ref(false)

const handleVerification = () => {
    navigateTo('/')
}

</script>