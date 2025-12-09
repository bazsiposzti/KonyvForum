<template>
  <nav class="main-navbar">

    <div class="navbar-container">

      <div class="logo-group">
        <img src="/book.png" alt="book logo" class="book-logo" />
        <h3><a href="#" class="navbar-logo">Könyvfórum</a></h3>
      </div>

      <ul class="navbar-items">
        <li><a href="#">Kezdőlap</a></li>
        <li>|</li>
        <!--Dísz nem biztos hogy kell-->
        <li><a href="#">Fórum</a></li>
        <li>|</li>
        <li><a href="#">Aktivitás</a></li>
      </ul>

    <div class="navbar-login">
      <button>Belépés</button>
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

/* Belépés/Regisztráció gomb */
.navbar-login {
  display: flex;
  gap: 0.5rem;
  margin-left: auto;
}

.navbar-login button {
  padding: 8px 20px;       
  border-radius: 6px;      
  border: none;
  cursor: pointer;
  font-weight: 600;        
  font-size: 14px;
  transition: all 0.2s ease; 
  font-family: inherit;   
}

.navbar-login button:first-child {
  background-color: #2ea44f; /* Átlátszó */
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.4); /* Halvány fehér keret */
}

.navbar-login button:first-child:hover {
  background-color: #2c974b;
  box-shadow: 0 2px 4px rgba(0,0,0 0.2);
  transform: translateY(-1px);
}

.navbar-login button:last-child {
  background-color: #e67e22; 
  color: #fff;
}

/* Regisztráció hover effekt */
.navbar-login button:last-child:hover {
  background-color: #d35400; 
  transform: translateY(-1px); 
  box-shadow: 0 4px 6px rgba(0,0,0,0.2); 
}

</style>
