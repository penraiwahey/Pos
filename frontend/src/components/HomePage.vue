<template>
  <div class="bg-white h-full">
    <div class="flex border-b border-gray-300">
      <div
        v-for="(tab, index) in tabs"
        :key="index"
        @click="activeTab = index"
        class="cursor-pointer px-4 py-2 relative"
      >
        <span :class="activeTab === index ? 'text-orange-500 font-semibold' : 'text-black'">
          {{ tab }}
        </span>
        <!-- เส้นข้างใต้ -->
        <span
          v-if="activeTab === index"
          class="absolute left-0 bottom-0 w-full h-0.5 bg-orange-500"
        ></span>
      </div>
    </div>

    <div class="p-4">
          <div class=" text-black">
  <div class="overflow-x-auto">
  <table class="table text-black">
    <!-- head -->
    <thead>
      <tr class=" text-black">
        <th></th>
        <th>Name</th>
        <th>Job</th>
        <th>Favorite Color</th>
      </tr>
    </thead>
    <tbody>
      <!-- row 1 -->
      <tr>
        <th>1</th>
        <td>Cy Ganderton</td>
        <td>Quality Control Specialist</td>
        <td>Blue</td>
      </tr>
      <!-- row 2 -->
      <tr>
        <th>2</th>
        <td>Hart Hagerty</td>
        <td>Desktop Support Technician</td>
        <td>Purple</td>
      </tr>
      <!-- row 3 -->
      <tr>
        <th>3</th>
        <td>Brice Swyre</td>
        <td>Tax Accountant</td>
        <td>Red</td>
      </tr>
    </tbody>
  </table>
</div>
</div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Table from '@/components/Table.vue'

const tabs = ['การจัดการใบรายการจัดส่ง', 'ตำแหน่งสินค้าคงคลัง', 'บันทึกการจัดการสินค้า','รับสินค้า','จัดการใบจัดซื้อ','ข้อมูลสินค้า','จัดการคำสั่งซื้อ','บันทึกการดาวน์โหลด']
const activeTab = ref(0)
</script>
