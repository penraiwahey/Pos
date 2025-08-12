<template>
  <div>
    <!-- Header section -->
    <header>
      <div class="drawer">
        <input id="my-drawer-3" type="checkbox" class="drawer-toggle" />
        <div class="drawer-content flex flex-col">
          <div class="navbar bg-base-300 w-full">
            <label for="my-drawer-3" aria-label="open sidebar" class="btn btn-square btn-ghost">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                class="inline-block h-6 w-6 stroke-current"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                ></path>
              </svg>
            </label>
            <div class="flex-1">
              <a class="btn btn-ghost text-xl">Pos <p class="text-indigo-600">Exemple</p></a>
            </div>
            <div class="flex gap-2">
              <input type="text" placeholder="Search" class="input input-bordered w-24 md:w-auto" />
            </div>
          </div>
        </div>
        <div class="drawer-side">
          <label for="my-drawer-3" aria-label="close sidebar" class="drawer-overlay"></label>
          <ul class="menu bg-base-200 min-h-full w-80 p-4">
            <li><a>หน้าหลัก</a></li>
            <li><a>สินค้า</a></li>
            <li><a>รายงาน</a></li>
            <li><a>ตั้งค่า</a></li>
            <li><a @click="handleLogout">ออกจากระบบ</a></li>
          </ul>
        </div>
      </div>
    </header>

    <!-- Main content area for the home page -->
    <main class="container mx-auto p-8 h-screen">
      <HomePage />
    </main>

    <!-- Footer section -->
    <footer class="footer footer-center p-4 bg-base-300 text-base-content mt-8">
      <div>
        <p>Pos Example</p>
        <p>Developed by : -</p>
        <p>Copyright © 2025 - All right reserved by Pos Example</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router' // ส่วนที่แก้ไข: นำเข้า useRouter
import HomePage from '@/components/icons/HomePage.vue'
const router = useRouter()

// ฟังก์ชันสำหรับออกจากระบบ
const handleLogout = () => {
  // ลบข้อมูลเซสชันออกจาก localStorage
  localStorage.removeItem('isLoggedIn')
  localStorage.removeItem('sessionExpires')
  
  // นำทางผู้ใช้กลับไปที่หน้าล็อกอิน
  router.push({ name: 'login' })
}
</script>

<style scoped>
/* You can add specific styles for this page here */
</style>
