<script setup>
import { ref } from 'vue';

const emit = defineEmits(['close'])

</script>

<template>
    <div class="login-form-dropdown">
      <div class="login-header">
          <h3>Bejelentkezés</h3>
          <span class="close-btn" @click="$emit('close')" title="Bezárás">✕</span>
      </div>
      
      <form @submit.prevent="handleSubmit">
        <div class="input-group">
            <h5>Felhasználónév</h5>
            <input type="text" v-model="username" placeholder="felhasználónév..">
        </div>
        <div class="input-group">
            <h5>Jelszó</h5>
            <input type="password" v-model="password" placeholder="jelszó..">
        </div>
        <button class="submit-btn">Bejelentkezés</button>
      </form>
  </div>
</template>


<style scoped>
.login-form-dropdown {
    position: absolute;
    top: 65px;
    right: 20px;
    width: 300px;
    background-color: #1c2538;
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.5);
    z-index: 1100;
    animation: fadeIn 0.2s ease-in-out;
}

.login-form-dropdown input {
    width: 100%;
    box-sizing: border-box;
    padding: 10px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background-color: #0d1117;
    color: white;
    font-family: inherit;
}

.login-form-dropdown input:focus {
    outline: none;
    border-color: #2ea44f;
}

.login-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    color: white;
    border-bottom: 1px solid rgba(255,255,255,0.1);
    padding-bottom: 10px;
}

.login-header h3 {
    margin: 0;
    font-size: 18px;
}

.close-btn {
    cursor: pointer;
    font-weight: bold;
    color: #8b949e;
    font-size: 18px;
    padding: 5px;
    transition: color 0.2s;
}

.close-btn:hover {
    color: white;
}

.input-group {
    margin-bottom: 15px;
}

.input-group label {
    display: block;
    color: #8b949e;
    font-size: 12px;
    margin-bottom: 5px;
    font-weight: 600;
}

.input-group h5 {
    color: #8b949e;
    margin: 0 0 5px 0; 
    font-size: 12px;
}

input {
    width: 100%;
    box-sizing: border-box;
    padding: 10px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background-color: #0d1117;
    color: white;
    font-family: inherit;
}

input:focus {
    outline: none;
    border-color: #2ea44f;
}



.submit-btn {
    width: 100%;
    padding: 10px;
    background-color: #2ea44f;
    color: white;
    border: none;
    border-radius: 6px;
    font-weight: bold;
    cursor: pointer;
    margin-top: 5px;
    transition: background-color 0.2s;
}

.submit-btn:hover {
    background-color: #2c974b;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 768px){
    .login-form-dropdown{
      top: 60px;
      right: 0;
      left: 0;
      width: 100%;
      border-radius: 0 0 15px 15px;
      border-left: none;
      border-right: none;
      box-shadow: 0 15px 30px rgba(0,0,0,0.7);
      box-sizing: border-box;
    }
    .login-form-dropdown,
    .submit-btn{
      padding: 12px;
      font-size: 16px;
    }
}
</style>
