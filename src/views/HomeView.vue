<template>
<div class="flex h-screen">
      <div class="bg-gray-700 h-full w-1/3 flex flex-col items-center justify-center">
      <p class="text-white text-3xl font-bold text-center">คำอธิบายหรือข้อความต้อนรับ<br/>เว็บไซต์ Ecommerce</p>
        <img src="@/assets/login-xh.png" alt="Logo" class="w-64 h-64 mt-20" />
      </div>
            <div class="flex flex-col items-center justify-cente login-container w-full  bg-white p-8">
            <p class="text-black font-bold text-3xl ">login</p>

            
                <input type="text" placeholder="Email address" class="input input-primary mb-6 mt-6 bg-white text-black" /> 
          
                <input type="text" placeholder="password" class="input input-primary mb-6 bg-white text-black" /> 
              <button class="btn btn-outline btn-accent">Login</button>
                <label class="label">
              <input type="checkbox" checked="checked" class="checkbox checkbox-primary" />
                  <p class="text-black mt-2">Remember me</p>
              </label>
      </div>
    </div>
</template>

<script setup  >

</script>

<style scoped>
.login-container {
    max-width: 400px;
    margin: 80px auto;
    padding: 32px;
    border: 1px solid #eee;
    border-radius: 8px;
    background: #fff;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
.login-form h2 {
    margin-bottom: 24px;
    text-align: center;
}
.form-group {
    margin-bottom: 16px;
}
.form-group label {
    display: block;
    margin-bottom: 6px;
    font-weight: 500;
}
.form-group input {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
}
button[type="submit"] {
    width: 100%;
    padding: 10px;
    background: #1976d2;
    color: #fff;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
}
button[type="submit"]:hover {
    background: #1565c0;
}
.error {
    color: #d32f2f;
    margin-top: 12px;
    text-align: center;
}
</style>