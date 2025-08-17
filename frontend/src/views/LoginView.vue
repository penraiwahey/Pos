
<template>
  <div class="flex h-screen bg-gray-100">
    <!-- Left panel with welcome message and image -->
    <div class="hidden md:flex bg-amber-500 h-full w-1/3 flex-col items-center justify-center p-8">

      <div class="flex flex-col items-center h-1/3 text-white mb-8">
        <div class="fixed top-5 left-5">
        <img src="@/assets/LOGO2.png" alt="Logo" class="w-24 h-24 radio border-white" />
        </div>
        <p class="text-white text-3xl font-bold text-center leading-relaxed">
          คำอธิบายหรือข้อความต้อนรับ<br/>เว็บไซต์ Ecommerce
        </p>
        <img src="@/assets/LOGO2.png" alt="Logo" class="w-64 h-64 mt-20 radio border-4 border-white" />

      </div>
      <div class="flex flex-col items-center justify-center h-1/3">
        <p class="text-white text-lg text-center mt-96">
          เข้าสู่ระบบเพื่อเริ่มต้นการใช้งานเว็บไซต์ของคุณ
        </p>
        <p class="text-white text-sm text-center">
          หากคุณยังไม่มีบัญชีผู้ใช้ สามารถลงทะเบียนได้ที่นี่
        </p>
      </div>
    </div>

    <!-- Right panel with login form -->
    <div class="flex flex-1 flex-col items-center justify-center p-8 login-container bg-white">
      <div class="flex justify-between">
        <p class="text-black font-bold text-4xl mb-6 w-1/2">Login</p>
        <div class="w-1/2 ml-30"></div>
        <select class="select w-28 bg-white text-black select-warning">
          <option>ไทย</option>
          <option>อังกฤษ</option>
        </select>
      </div>
      
      
      <form @submit.prevent="handleLogin" class="flex flex-col w-full max-w-sm">
        <input 
          type="email" 
          placeholder="Email address" 
          class="input input-bordered w-full rounded-lg px-4 py-3 mb-6 bg-white text-black border border-gray-300 focus:outline-none focus:ring-2 focus:ring-yellow-500"
          v-model="email"
        /> 
        <div class="relative w-full">
          <input 
            :type="showPassword ? 'text' : 'password'"
            placeholder="Password" 
            class="input input-bordered w-full rounded-lg px-4 py-3 mb-6 bg-white text-black border border-gray-300 focus:outline-none focus:ring-2 focus:ring-yellow-500 pr-10" 
            v-model="password"
          />
           <button 
              type="button" 
              @click="togglePasswordVisibility" 
              class="absolute inset-y-0 right-0 flex items-center px-4 text-gray-600 hover:text-gray-800"
              aria-label="Toggle password visibility"
            >
              <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
          </button>
        </div>
          

        <div class="flex justify-between items-center mb-6">
          <label class="label cursor-pointer flex items-center">
            <input type="checkbox" class="checkbox checkbox-warning mr-2" v-model="rememberMe" /> <!-- แก้ไขตรงนี้ -->
            <p class="text-black text-sm">Remember me</p>
          </label>
          <a href="#" class="text-sm text-orange-500 hover:underline">Forgot password?</a>
        </div>
        
        <button type="submit" class="btn bg-orange-600 hover:bg-orange-700 text-white font-bold py-3 px-4 rounded-lg shadow-md transition-colors duration-200">
          Login
        </button>
        <p class="text-center text-gray-600 mt-4">
          Don't have an account? 
          <a href="#" class="text-orange-500 hover:underline">Sign up</a>
        </p>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue' // เพิ่ม onMounted
import { useRouter } from 'vue-router'
import Swal from 'sweetalert2'


const email = ref('')
const password = ref('')
const rememberMe = ref(false) 
const showPassword = ref(false);

const router = useRouter()
function togglePasswordVisibility() {
  showPassword.value = !showPassword.value;
}

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
  if (email.value === 'E@E.EE' && password.value === 'Ka74000') {
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

<style scoped>
/* You can keep your custom styles here */
.login-container {
  max-width: 400px;
  margin: auto;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.inset-y-0 {
  top: 0;
  bottom: 0;
}

button.absolute {
    transform: translateY(-12px); 
}
</style>