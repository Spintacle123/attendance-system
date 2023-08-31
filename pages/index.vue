<template>
    <main class="flex flex-col items-center gap-4 py-6 px-8 mt-[5rem] bg-white">
<!-- SUMMARY SECTION-->       
      <section class="flex items-center grow gap-4 py-3 px-6 rounded-lg border-2 border-custom-gray w-[100%]">
        <div class="flex items-center gap-4 p-4 w-[40%]">
            <Icon icon="mdi:megaphone" :style="{ fontSize: '64px', color: 'var(--custom-red)' }"/>
            <span class="font-bold text-2xl text-[#000]">Today, 23 August 2023</span>
        </div>
    <!-- Cards -->
        <VCard title="Total Employees" total="50" icon="clarity:employee-solid"/>
        <VCard title="On Time" total="25" icon="mdi:clock"/>
        <VCard title="Late In" total="20" icon="material-symbols:assignment-late" color="var(--custom-red)"/>
        <VCard title="Absent" total="5" icon="material-symbols:close" color="var(--custom-red)"/>
      </section>  
<!-- EMPLOYEE ATTENDANCE SECTION -->
      <section class="flex flex-col items-center grow rounded-lg border-2 border-custom-gray w-[100%]">
    <!-- Employee attendance header -->
        <header class="flex items-center gap-6 py-4 px-6 w-[100%]">
            <div class="grow">
                <h2 class="font-bold text-2xl">Employee Attendance</h2>
                <span class="text-sm ">Keep track of the employee attendance on a daily basis</span>
            </div>
            <div class="flex gap-4 text-sm font-bold text-white">
                <VButton title="Export" icon="solar:upload-outline" @handleClick="cons"/>
                <VButton title="Add Employee" icon="material-symbols:add"  @handleClick=""/>
                <VButton title="23 August 2023" icon="solar:calendar-linear" styled="secondary" @handleClick=""/>
                
                <input type="date" class="flex items-center gap-4 py-3 px-6 rounded-lg text-black border border-custom-gray "/>   
            </div>
        </header>
    <!-- Filtering buttons -->
        <div class="flex items-center gap-6 py-4 px-6 w-[100%] border-t">
            <div class="grow flex gap-4 text-sm font-bold text-white ">
                <VButton title="All Employee"  @handleClick="cons"/>
                <VButton title="Interns" @handleClick="cons" styled="secondary"/>
            </div>
            <div class="flex gap-4 text-sm font-bold text-white">
                <div class="flex items-center gap-4 p-3 rounded-lg border border-custom-gray text-black">
                    <Icon icon="ant-design:search-outlined" :style="{  color: '#a3a3a3'}"/>
                    <input type="text" placeholder="Search" class="focus:outline-none"  v-model="searchText"/>
                </div>
                <VButton icon="ion:filter" @handleClick="cons" styled="secondary"/>
            </div>
        </div>
    <!-- Table -->
        <div class="w-[100%] border-t h-[40vh] overflow-auto">
            <table class="table w-[100%] ">
                <thead class="font-bold text-[15px] text-[#808080] bg-[#F8F8F8] sticky top-0">
                    <tr class="text-left">
                        <th class="py-3 px-6">Employee ID</th>
                        <th class="py-3 px-6">Employee</th>
                        <th class="py-3 px-6">Date</th>
                        <th class="py-3 px-6">Shift</th>
                        <th class="py-3 px-6">Time In</th>
                        <th class="py-3 px-6">Time Out</th>
                        <th class="py-3 px-6">Overtime</th>
                        <th class="py-3 px-6">Work Time</th>
                        <th class="py-3 px-6">Status</th>
                        <th class="py-3 px-2"></th>
                        
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in filteredItemsByName.slice(0,6)" class="text-[15px] hover:bg-red-50 cursor-pointer ">
                        <td class="py-3 px-6">{{item.id}}</td>
                        <td class="flex gap-4 py-3 px-6">
                            <img :src="item.img" class="rounded-full w-[40px] h-[40px] object-cover"/> 
                            <h4 class="flex flex-col font-bold text-black">
                                {{item.name}} 
                                <span class="font-normal text-sm text-[#667085]">{{ item.role }}</span>
                            </h4>
                        </td>
                        <td class="py-3 px-6 min-w-[10em]">23 August 2023</td>
                        <td class="py-3 px-6"></td>
                        <td class="py-3 px-6">{{ item.timeIn }} </td>
                        <td class="py-3 px-6">{{ item.timeOut }} </td>
                        <td class="py-3 px-6">{{ item.overTime }} hrs</td>
                        <td class="py-3 px-6">{{ item.workTime }} hrs</td>
                        <td class="py-3 px-6">{{ item.status }} </td>
                        <td class="py-3 px-2"><VButton icon="ri:delete-bin-line" iconBtn="iconBtn"/></td>
                    </tr>
                </tbody>
            </table>
        </div>
    <!-- Pagination buttons -->
        <div class="flex items-center justify-between gap-6 py-4 px-6 w-[100%] border-t">
            <span class="font-semibold text-sm">Page 1 of 20 </span>
            <div class="flex gap-4">
                <VButton styled="secondarySmallBtn" title="Previous"/>
                <VButton styled="secondarySmallBtn" title="Next"/>
            </div>
        </div>
      </section>
    </main>
</template>

<script setup>

import { Icon } from '@iconify/vue';
import { ref ,computed } from 'vue'

const searchText = ref("")

const cons = () => {
  console.log('Button clicked!');
};


const filteredItemsByName = computed(() => {
    if (!searchText.value) {
        return items.value;
    }
    return items.value.filter((item) =>
        item.name.toLowerCase().includes(searchText.value.toLowerCase())||
        item.role.toLowerCase().includes(searchText.value.toLowerCase())
    );
});

const items = ref([
    {
        id: 1001,
        img:'data:image/jpeg;base64,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',
        name: 'Sam Molin',
        role: 'Back End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 1002,
        name: 'Claire Lim',
        img:'data:image/jpeg;base64,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',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 1003,
        name: 'Manuel Solis',
        img: 'https://images.pexels.com/photos/5378700/pexels-photo-5378700.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 1004,
        name: 'Sam Molin',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 1005,
        name: 'Manuel Solis',
        img: 'https://images.pexels.com/photos/5378700/pexels-photo-5378700.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 1006,
        name: 'Sam Molin',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 1005,
        name: 'Manuel Solis',
        img: 'https://images.pexels.com/photos/5378700/pexels-photo-5378700.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    },
    {
        id: 100,
        name: 'Sam Molin',
        role: 'Front End Developer',
        date: '23 August 2023',
        shift: '',
        timeIn: '9:00',
        timeOut: '8:00',
        overTime: '0.00',
        workTime: '05.00',
        status: 'Half Day'
    }
])
</script>