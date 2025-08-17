<template>
  <div>
    <div class="flex justify-center min-h-screen bg-gray-100">
      <div class="flex flex-col justify-center items-center">
        <ul class="menu bg-orange-500 h-full">
          <li class="mb-2">
            <div class="flex flex-col items-center justify-center h-12 w-15">
              <img src="@/assets/logo.png" alt="Logo" class="w-full h-full radio" />
            </div>
          </li>
          <div class="bg-white h-0.5 w-full rounded"></div>
          <li class="flex flex-col items-center justify-center h-12 w-15">
            <a>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" />
              </svg>
            </a>
          </li>
          <li class="flex flex-col items-center justify-center h-12 w-15">
            <a>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </a>
          </li>
          <li class="flex flex-col items-center justify-center h-12 w-15">
            <a>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
              </svg>
            </a>
          </li>
        </ul>
      </div>

      <div class="mx-auto h-screen w-screen">
        <div class="bg-white h-full">
          <div class="flex border-b border-gray-300">
            <div
              v-for="(tab, index) in tabs"
              :key="index"
              @click="activeTab = index"
              class="cursor-pointer px-4 py-2 relative">
              <span :class="activeTab === index ? 'text-orange-500 font-semibold' : 'text-black'">
                {{ tab }}
              </span>
              <!-- เส้นข้างใต้ -->
              <span
                v-if="activeTab === index"
                class="absolute left-0 bottom-0 w-full h-0.5 bg-orange-500">
              </span>
            </div>
          </div>

          <div class="p-4">
            <div class="text-black">
              <div class="overflow-x-auto">
                <table class="table text-black">
                  <!-- head -->
                  <thead>
                    <tr class="text-black">
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
      </div>
    </div>

    <!-- Footer section -->
    <!-- <footer class="footer footer-center p-4 bg-base-300 text-base-content ">
      <div>
        <p>Pos Example</p>
        <p>Developed by : -</p>
        <p>Copyright © 2025 - All right reserved by Pos Example</p>
      </div>
    </footer> -->
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
const router = useRouter()

// ฟังก์ชันสำหรับออกจากระบบ
const handleLogout = () => {
  localStorage.removeItem('isLoggedIn')
  localStorage.removeItem('sessionExpires')
  router.push({ name: 'login' })
}

const tabs = ['การจัดการใบรายการจัดส่ง', 'ตำแหน่งสินค้าคงคลัง', 'บันทึกการจัดการสินค้า', 'รับสินค้า', 'จัดการใบจัดซื้อ', 'ข้อมูลสินค้า', 'จัดการคำสั่งซื้อ', 'บันทึกการดาวน์โหลด']
const activeTab = ref(0)
</script>

<style scoped>
/* You can add specific styles for this page here */
</style>
