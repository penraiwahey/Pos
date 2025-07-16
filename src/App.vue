<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  
<header>
<div class="drawer">
  <input id="my-drawer-3" type="checkbox" class="drawer-toggle" />
  <div class="drawer-content flex flex-col">
    <!-- Navbar -->
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
      <!-- Sidebar content here -->
      <li><a>หน้าหลัก</a></li>
      <li><a>สินค้า</a></li>
      <li><a>รายงาน</a></li>
      <li><a>ตั้งค่า</a></li>
      <li><a>ออกจากระบบ</a></li>
    </ul>
  </div>
</div>
  </header>
  <main class="min-h-screen">
    <RouterView />
  </main>

<footer class="footer footer-center p-4 bg-base-300 text-base-content">
    <div>
      <p>Pos Example</p>
      <p>Developed by Yangpara</p>
      <p>Copyright © 2025 - All right reserved by Pos Example</p>
    </div>
</footer>

</template>

