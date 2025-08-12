<script setup>
import { ref, onMounted } from 'vue' // เพิ่ม onMounted
import { useRouter } from 'vue-router'
import Swal from 'sweetalert2'


const email = ref('')
const password = ref('')
const rememberMe = ref(false) 


const router = useRouter()


onMounted(() => {
  const storedSession = localStorage.getItem('isLoggedIn')
  const sessionExpiration = localStorage.getItem('sessionExpires')
  
  // ตรวจสอบว่ามีเซสชันและยังไม่หมดอายุ
  if (storedSession && new Date() < new Date(sessionExpiration)) {
    console.log('Session found, redirecting to home...')
    router.push({ name: 'home' })
  }
})

// ฟังก์ชันสำหรับจัดการการล็อกอิน
const handleLogin = () => {
  // จำลองการตรวจสอบข้อมูลการล็อกอิน
  if (email.value === 'user@example.com' && password.value === 'password123') {
    // ถ้าล็อกอินสำเร็จ
    Swal.fire({
      title: 'สำเร็จ!',
      text: 'คุณเข้าสู่ระบบเรียบร้อยแล้ว',
      icon: 'success',
      timer: 2000,
      showConfirmButton: false
    }).then(() => {
      // ถ้า checkbox "Remember me" ถูกเลือก
      if (rememberMe.value) {
        console.log('Remember me is checked. Saving session...')
        // ตั้งค่าวันหมดอายุของเซสชัน (30 วัน)
        const expirationDate = new Date()
        expirationDate.setDate(expirationDate.getDate() + 30)

        // เก็บสถานะการล็อกอินและวันหมดอายุไว้ใน localStorage
        localStorage.setItem('isLoggedIn', 'true')
        localStorage.setItem('sessionExpires', expirationDate.toISOString())
      }

      // เปลี่ยนหน้าไปยัง HomeView
      router.push({ name: 'home' })
    })
  } else {
    // ถ้าล็อกอินไม่สำเร็จ
    Swal.fire({
      title: 'ข้อผิดพลาด!',
      text: 'อีเมลหรือรหัสผ่านไม่ถูกต้อง',
      icon: 'error',
      confirmButtonText: 'ลองอีกครั้ง'
    })
  }
}
</script>

<template>
  <div class="flex h-screen bg-gray-100">
    <!-- Left panel with welcome message and image -->
    <div class="hidden md:flex bg-gray-700 h-full w-1/3 flex-col items-center justify-center p-8 rounded-r-3xl">
      <p class="text-white text-3xl font-bold text-center leading-relaxed">
        คำอธิบายหรือข้อความต้อนรับ<br/>เว็บไซต์ Ecommerce
      </p>
      <img src="https://placehold.co/256x256/2d3748/ffffff?text=Logo" alt="Logo" class="w-64 h-64 mt-20" />
    </div>

    <!-- Right panel with login form -->
    <div class="flex flex-1 flex-col items-center justify-center p-8 login-container bg-white">
      <p class="text-black font-bold text-4xl mb-6">Login</p>
      
      <form @submit.prevent="handleLogin" class="flex flex-col w-full max-w-sm">
        <input 
          type="email" 
          placeholder="Email address" 
          class="input input-bordered w-full rounded-lg px-4 py-3 mb-6 bg-white text-black border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
          v-model="email"
        /> 
        
        <input 
          type="password" 
          placeholder="Password" 
          class="input input-bordered w-full rounded-lg px-4 py-3 mb-6 bg-white text-black border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" 
          v-model="password"
        /> 

        <div class="flex justify-between items-center mb-6">
          <label class="label cursor-pointer flex items-center">
            <input type="checkbox" class="checkbox checkbox-primary mr-2" v-model="rememberMe" /> <!-- แก้ไขตรงนี้ -->
            <p class="text-black text-sm">Remember me</p>
          </label>
          <a href="#" class="text-sm text-blue-500 hover:underline">Forgot password?</a>
        </div>
        
        <button type="submit" class="btn btn-primary bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-4 rounded-lg shadow-md transition-colors duration-200">
          Login
        </button>
      </form>
    </div>
  </div>
</template>

<style scoped>
/* You can keep your custom styles here */
.login-container {
  max-width: 400px;
  margin: auto;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}
</style>