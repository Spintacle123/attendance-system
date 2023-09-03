<template>
    <VDropdown title="Export" icon="solar:upload-outline" @handleClick="handleDropdownItemClick">
      <div class="flex flex-col text-[12px] font-bold">
        <div class="flex items-center gap-4 p-4 hover:bg-red-100 cursor-pointer"  @click="exportToWord"><Icon icon="vscode-icons:file-type-word" /> Export to Word</div>
        <div class="flex items-center gap-4 p-4 hover:bg-red-100 cursor-pointer"  @click="exportToWord"><Icon icon="vscode-icons:file-type-excel" /> Export to Excel</div>
        <div class="flex items-center gap-4 p-4 hover:bg-red-100 cursor-pointer"  @click="generatePDF(items)"><Icon icon="vscode-icons:file-type-pdf2" /> Export to PDF</div>
      </div>
    </VDropdown>
  </template>
  
  <script setup>
  defineProps(['items'])
  import { jsPDF } from "jspdf";
  import autoTable from 'jspdf-autotable'
  import { Icon } from '@iconify/vue';

    const generatePDF= (items) =>{
      const doc = new jsPDF();
      
      doc.setFontSize(18);
      doc.text("Attendance Summary", 10, 20);

      const columns = ["ID", "Name", "Role", "Date", "Shift", "Time In", "Time Out", "Overtime", "Work Time", "Status"];
      const rows = items.map(item => [
        item.id,
        item.name,
        item.role,
        item.date,
        item.shift,
        item.timeIn,
        item.timeOut,
        item.overTime,
        item.workTime,
        item.status
      ]);

      
      doc.autoTable({
        head: [columns],
        body: rows,
        startY: 26, 
        styles: {
          fontSize: 10,
          cellPadding: 2,
        },
        headStyles :{fillColor : [105,105,105]},
        columnStyles: {
          1: { cellWidth: 20 }, 
        },
      });

      doc.save("intern_data.pdf");
    }
    const exportToWord= () =>{
      
      console.log("fff")
    }
    const exportToPDF= ()=> {
      console.log("dfdf")
    }
 
  </script>
  