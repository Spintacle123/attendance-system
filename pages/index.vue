<template>
    <VHeader/>
    <main class="flex flex-col items-center gap-4 py-6 px-8 mt-[5rem] bg-white">
<!-- SUMMARY SECTION-->       
      <section class="flex flex-col items-center grow gap-4 py-3 px-6 rounded-lg border-2 border-custom-gray w-[100%] sm:flex-row">
        <div class="flex items-center gap-4 p-4 w-full sm:w-[40%]">
            <Icon icon="mdi:megaphone" :style="{ fontSize: '64px', color: 'var(--custom-red)' }"/>
            <span class="font-bold text-lg sm:text-2xl text-[#000]">{{ formattedDate}}</span>
        </div>
    <!-- Cards -->
        <div class="flex items-center grow gap-4 w-[100%] sm:w-[60%] flex-wrap">
            <VCard title="Total Employees" total="50" icon="clarity:employee-solid"/>
            <VCard title="On Time" total="25" icon="mdi:clock"/>
            <VCard title="Late In" total="20" icon="material-symbols:assignment-late" color="var(--custom-red)"/>
            <VCard title="Absent" total="5" icon="material-symbols:close" color="var(--custom-red)"/>
        </div>

      </section>  
<!-- EMPLOYEE ATTENDANCE SECTION -->
      <section class="flex flex-col items-center grow rounded-lg border-2 border-custom-gray w-[100%]">
    <!-- Employee attendance header -->
        <header class="flex flex-col items-center gap-6 py-4 px-6 w-[100%] sm:flex-row">
            <div class="grow">
                <h2 class="font-bold text-2xl">Employee Attendance</h2>
                <span class="text-sm ">Keep track of the employee attendance on a daily basis</span>
            </div>
            <div class="flex gap-4 text-sm font-bold text-white">
                <Export :items="items"/>
                <VDropdown title="Add Employee" icon="material-symbols:add" >
                    <div class="flex items-center gap-4 p-4 hover:bg-red-100 cursor-pointer"  @click="exportToWord"><Icon icon="gg:list" /> Directly Add</div>
                    <div class="flex items-center gap-4 p-4 hover:bg-red-100 cursor-pointer"  @click="exportToWord"><Icon icon="cib:gmail" /> Send to Email</div>
                </VDropdown>
             <!--- <VButton title="23 August 2023" icon="solar:calendar-linear" styled="secondary" @handleClick=""/>
             -->
                <input type="date"  v-model="selectedDate" class="flex items-center gap-4 py-3 px-6 rounded-lg text-black border border-custom-gray focus:outline-none"/>   
            </div>
        </header>
    <!-- Filtering buttons -->
        <div class="flex items-center gap-6 py-4 px-6 w-[100%] border-t">
            <div class="grow flex gap-4 text-sm font-bold text-white ">
                <VButton title="All Employee"  @handleClick="()=>changeData(employeeData)"  />
                <VButton title="Interns" @handleClick="()=>changeData(internData)" styled="secondary"/>
            </div>
            <div class="flex gap-4 text-sm font-bold text-white">
                <div class="flex items-center gap-4 p-3 rounded-lg border border-custom-gray text-black">
                    <Icon icon="ant-design:search-outlined" :style="{  color: '#a3a3a3'}"/>
                    <input type="text" placeholder="Search" class="focus:outline-none"  v-model="searchText"/>
                </div>
                <VButton icon="ion:filter" @handleClick="" styled="secondary"/>
            </div>
        </div>
    <!-- Table -->
        <div class="w-[100%] border-t h-[100vh] overflow-auto sm:h-[40vh]">
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
            <!-- table row -->
                    <tr  @click="() => handleRowClick(item)" v-for="item in filteredItemsByName" class="text-[15px] hover:bg-red-50 cursor-pointer ">
                        <td class="py-3 px-6">{{item.id}}</td>
                        <td class="flex gap-4 py-3 px-6">
                            <img :src="item.img" class="rounded-full w-[40px] h-[40px] object-cover"/> 
                            <h4 class="flex flex-col font-bold text-black">
                                {{item.name}} 
                                <span class="font-normal text-sm text-[#667085]">{{ item.role }}</span>
                            </h4>
                        </td>
                        <td class="py-3 px-6 min-w-[10em]">{{ item.date }}</td>
                        <td class="py-3 px-6">
                            <select id="shift" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:outline-none block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                            <option :selected="item.shift === 'MS' && true" value="MS">Morning Shift</option>
                            <option :selected="item.shift === 'AS' && true" value="AS">Afternoon Shift</option>
                            <option :selected="item.shift === 'NS' && true" value="NS">Night Shift</option>
                            </select></td>
                        <td class="py-3 px-6">{{ item.timeIn }} </td>
                        <td class="py-3 px-6">{{ item.timeOut }} </td>
                        <td class="py-3 px-6">{{ item.overTime }} hrs</td>
                        <td class="py-3 px-6">{{ item.workTime }} hrs</td>
                        <td class="py-3 px-6 font-bold" :style="{ color: item.status === 'Half Day' ? '#DAAD0D' : item.status === 'Present' ? '#2E8F00' :'#E42323'  }">{{ item.status }}</td>
                        <td class="py-3 px-2"><VButton icon="ri:delete-bin-line" iconBtn="iconBtn" @handleClick="() => {delModalOpen = true;}"/></td>
                    </tr>
                </tbody>
            </table>
        </div>
    <!-- Pagination buttons -->
        <div class="flex items-center justify-between gap-6 py-4 px-6 w-[100%] border-t">
            <span class="font-semibold text-sm">Page {{ currentPage }} of {{ totalPages }} </span>
            <div class="flex gap-4">
                <VButton styled="secondarySmallBtn" title="Previous"  @handleClick="currentPage > 1 && currentPage-- "/>
                <VButton styled="secondarySmallBtn" title="Next" @handleClick="currentPage < totalPages && currentPage++"/> 
            </div>
        </div>
      </section>
      <VModal v-if="delModalOpen" @handle-click="handleDelete(selectedID)" @close-modal="delModalOpen = false" title="Delete Employee" subtitle="You are going to delete an employee. Are you sure?" color="#E42326" img="/img/delete.png" icon="ri:delete-bin-line" name="Yes, Delete" secondBtn="No, Keep It"/>

    </main>
</template>


<script setup>

import { Icon } from '@iconify/vue';
import { ref ,computed } from 'vue'
import {employeeData, internData} from '../components/index.js'

const searchText = ref("")
const delModalOpen=ref(false)
const items = ref(employeeData)
const selectedID = ref()

// functions for searching and pagination
const currentPage = ref(1);
const itemsPerPage = 6;

const filteredItemsByName = computed(() => {
    const startIndex = (currentPage.value - 1) * itemsPerPage;
    const endIndex = startIndex + itemsPerPage;

    if (!searchText) {
        return items.value.slice(startIndex, endIndex);
    }
    return items.value.filter((item) =>
        item.name.toLowerCase().includes(searchText.value.toLowerCase()) ||
        item.role.toLowerCase().includes(searchText.value.toLowerCase())
    ).slice(startIndex, endIndex);
});

const totalPages =  computed(()=>{
    return Math.ceil(items.value.length / itemsPerPage)
});


// function to toggle between employees and interns table
const changeData = (data) => {
    currentPage.value = 1
    items.value= data
}


const handleRowClick = (item)=>{
    selectedID.value= item

    console.log(selectedID.name)
}

// Get formatted date
const monthNames = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
const currentDate = new Date();
const day = currentDate.getDate();
const month = currentDate.getMonth();
const year = currentDate.getFullYear();
const formattedDate = `Today, ${day} ${monthNames[month]} ${year}`;
const selectedDate=  new Date().toISOString().substr(0, 10)


const handleDelete = (item) => {
    delModalOpen.value = false
    const index = items.value.findIndex(emp => emp.id === item.id);

    if (index > -1) {
        items.value.splice(index, 1);
        clickedRow.value = null;
    }
};
</script>
