<template>
    <main class="flex flex-col items-center gap-4 py-6 px-8 bg-white">
 <!-- summary div-->       
      <div class="flex items-center grow gap-4 py-3 px-6 rounded-lg border-2 border-custom-gray w-[100%]">
        <div class="flex items-center gap-4 p-4 w-[40%]">
            <Icon icon="mdi:megaphone" :style="{ fontSize: '64px', color: '#E42323' }"/>
            <span class="font-bold text-2xl text-[#000]">Today, 23 August 2023</span>
        </div>
        <VCard title="Total Employees" total="50" icon="clarity:employee-solid"/>
        <VCard title="On Time" total="25" icon="mdi:clock"/>
        <VCard title="Late In" total="20" icon="material-symbols:assignment-late" color="#E42323"/>
        <VCard title="Absent" total="5" icon="material-symbols:close" color="#E42323"/>
      </div>  
<!-- employee attendance div -->
      <div class="flex flex-col items-center grow rounded-lg border-2 border-custom-gray w-[100%]">
        <div class="flex items-center gap-6 py-4 px-6 w-[100%]">
            <div class="grow">
                <h2 class="font-bold text-2xl">Employee Attendance</h2>
                <span class="text-sm ">Keep track of the employee attendance on a daily basis</span>
            </div>
            <div class="flex gap-4 text-sm font-bold text-white">
                <VButton title="Export" icon="solar:upload-outline" @handleClick="cons"/>
                <VButton title="Add Employee" icon="material-symbols:add"  @handleClick=""/>
                <VButton title="23 August 2023" icon="material-symbols:add" styled="true" @handleClick=""/>
              
            </div>
        </div>
        <div class="flex items-center gap-6 py-4 px-6 w-[100%] border-t">
            <div class="grow flex gap-4 text-sm font-bold text-white ">
                <VButton title="All Employee" icon="solar:upload-outline" @handleClick="cons"/>
                <VButton title="Interns" icon="solar:upload-outline" @handleClick="cons" styled="true"/>
            </div>
            <div class="flex gap-4 text-sm font-bold text-white">
                <div class="flex items-center gap-4 p-3 rounded-md border border-custom-gray text-black">
                    <Icon icon="ant-design:search-outlined" :style="{  color: '#a3a3a3'}"/>
                    <input type="text" placeholder="Search" class="focus:outline-none"/>
                </div>
                <VButton icon="ion:filter" @handleClick="cons" styled="true"/>
            </div>
        </div>
      </div>
      
    </main>
</template>
<script setup>
import { Icon } from '@iconify/vue';
const cons = () => {
  console.log('Button clicked!');
};
</script>