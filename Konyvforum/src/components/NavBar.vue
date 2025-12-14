<script setup>
    import { ref } from 'vue';

    const isMenuOpen = ref(false)
    // const loggedIn = ref(false)
    const loginClicked = ref(false)

    function toggleMenu(){
        isMenuOpen.value = !isMenuOpen.value;
    }

    function toggleLogin(){
      loginClicked.value = !loginClicked.value;
    }

    // const toggleDevMode = () => {
    //   loggedIn.value = !loggedIn.value
    // }

    const user = {
      nev: 'TesztElek',
      avatar: 'https://i.pravatar.cc/150?img=32'
    }
</script>
<!-- ötlet: alulra rakni navbart mobil nézetben -->
<template>
  <nav class="main-navbar">

    <div class="navbar-container">

      <div class="logo-group">
        <img src="/book.png" alt="book logo" class="book-logo" />
        <h3><a href="#" class="navbar-logo">Könyvfórum</a></h3>
      </div>

      <ul class="navbar-items desktop-view">
        <li><a href="#">Kezdőlap</a></li>
        <li>|</li>
        <!--Dísz nem biztos hogy kell-->
        <li><a href="#">Fórum</a></li>
        <li>|</li>
        <li><a href="#">Aktivitás</a></li>
      </ul>

    <div class="navbar-center desktop-view">
        <div class="search-bar">
          <input type="text" placeholder="Keresés könyv, szerző vagy ISBN alapján...">
          <span class="search-icon"></span>
        </div>
      </div>

    <div class="navbar-login desktop-view" v-if="!loginClicked">
      <button @click="toggleLogin">Belépés</button>
      <button>Regisztráció</button>
    </div>
    
    <div class="login-form-dropdown" v-if="loginClicked">
      <div class="login-header">
          <h3>Bejelentkezés</h3>
          <span class="close-btn" @click="toggleLogin" title="Bezárás">✕</span>
      </div>
      <form action="submit">
        <div class="input-group">
            <label>Felhasználónév</label>
            <input type="text" placeholder="Írd be a neved...">
        </div>
        <div class="input-group">
            <label>Jelszó</label>
            <input type="password" placeholder="••••••••">
        </div>
        <button class="submit-btn">Belépés</button>
      </form>
    </div>

    <div class="hamburger" @click="toggleMenu">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
    </div>
    </div>

    <div class="mobile-menu" v-if="isMenuOpen">
      <div class="mobile-search"></div>
        <a href="#" @click="toggleMenu">Kezdőlap</a>
        <a href="#" @click="toggleMenu">Fórum</a>
        <a href="#" @click="toggleMenu">Aktivitás</a>

        <div class="mobile-buttons">
            <button @click="toggleLogin(); toggleMenu()">Belépés</button>
            <button>Regisztráció</button>
        </div>
    </div>
  </nav>
</template>

<style scoped>

/* logó kép */
.book-logo {
  margin-right: 10px;
  height: 35px;
  width: auto;
}

/* navbar beállítás */
.main-navbar {
  background-color: #1c2538;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  z-index: 1000;
}

/* belső tartalom beállítása */
.navbar-container {
  width: 100%;
  padding: 0 20px;
  height: 60px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  position: relative;
}

/* logó + könyvfórum kiiratás */
.logo-group {
  display: flex;
  align-items: center;
  text-decoration: none;
  gap: 10px;
}

.logo-group a {
  color: #fff;
  text-decoration: none;
}
/* navbarnak tartalma */
.navbar-items {
  list-style-type: none;
  display: flex;
  gap: 1rem;
  color: #fff;
}

.navbar-items a {
  color: #fff;
  text-decoration: none;
}

/* Keresés mező */
.navbar-center {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: auto;
}

.navbar-center input{
  width: 400px;
  padding: 8px 12px;
  border-radius: 20px;
  border: 1px solid rgba(255,255,255,0.1);
  background-color: #121826;
  color: white;
  outline: none;
}

.navbar-center input:focus{
  border-color: #2ea44f;
}

/* Belépés/Regisztráció gomb */
.navbar-login {
  display: flex;
  gap: 0.5rem;
  margin-left: auto;
}

.navbar-login button,
.mobile-buttons button {
  padding: 8px 20px;       
  border-radius: 6px;      
  border: none;
  cursor: pointer;
  font-weight: 600;        
  font-size: 14px;
  transition: all 0.2s ease; 
  font-family: inherit;   
}

.navbar-login button:first-child,
.mobile-buttons button:first-child {
  background-color: #2ea44f; /* Átlátszó */
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.4); /* Halvány fehér keret */
}

.navbar-login button:first-child:hover {
  background-color: #2c974b;
  box-shadow: 0 2px 4px rgba(0,0,0 0.2);
  transform: translateY(-1px);
}

.navbar-login button:last-child,
.mobile-buttons button:last-child {
  background-color: #e67e22; 
  color: #fff;
}

/* Regisztráció hover effekt */
.navbar-login button:last-child:hover {
  background-color: #d35400; 
  transform: translateY(-1px); 
  box-shadow: 0 4px 6px rgba(0,0,0,0.2); 
}

/* mobilos rész */
.hamburger {
    display: none;
    cursor: pointer;
    margin-left: auto;
    flex-direction: column;
    gap: 5px;
}

.bar{
    display: block;
    width: 25px;
    height: 3px;
    background-color: white;
    border-radius: 3px;
}

.mobile-menu{
    background-color: #171e2e;
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 15px;
    border-top: 1px solid rgba(255,255,255,0.1);
    box-shadow: 0 10px 15px rgba(0,0,0,0.3);
}

.mobile-menu a {
  color: white;
  text-decoration: none;
  font-size: 16px;
  padding: 10px 0;
  border-bottom: 1px solid rgba(255,255,255,0.05);
}

.mobile-buttons {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 10px;
}

.mobile-buttons button {
  width: 100%; 
}

@media (max-width: 768px){
    .desktop-view {
        display: none !important;
    }
    .hamburger{
        display: flex;
    }

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

@media (hover: hover) {
    .navbar-login button:first-child:hover,
    .mobile-buttons button:first-child:hover {
        background-color: #2c974b;
        box-shadow: 0 2px 4px rgba(0,0,0, 0.2);
        transform: translateY(-1px);
    }
    .navbar-login button:last-child:hover,
    .mobile-buttons button:last-child:hover {
        background-color: #d35400; 
        transform: translateY(-1px); 
        box-shadow: 0 4px 6px rgba(0,0,0,0.2); 
    }
    .navbar-items a:hover,
    .mobile-menu a:hover {
        opacity: 0.8;
    }
}

.mobile-search input{
  width: 100%;
  padding: 10px;
  border-radius: 6px;
  border: 1px solid rgba(255,255,255,0.1);
  background-color: #0d1117;
  color: white;
  color: white;
  box-sizing: border-box;
  margin-bottom: 10px;
}

/* Belépés mező ha rákattintva van */
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
/* bejelentkezés gomb */
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

/* Animáció a megjelenéshez */
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
}

/* Ha a képernyő túl kicsi a keresőnek középen, elrejtjük vagy átméretezzük */
@media (max-width: 1100px) {
    .navbar-center input {
        width: 250px;
    }
}

</style>
