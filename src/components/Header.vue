<template>
  <header>
    <nav>
      <div class="logo">
        <img src="../../src/assets/Logo White.svg" alt="Logo" />
      </div>
      <ul class="nav-menu">
        <li><a href="#">HOME</a></li>
        <li><a href="#">OUR SCREENS</a></li>
        <li><a href="#">SCHEDULE</a></li>
        <li><a href="#">MOVIE LIBRARY</a></li>
        <li><a href="#">LOCATION & CONTACT</a></li>
        <li><a href="#"><img src="../../src/assets/Menu-White.svg" alt="Menu Icon" /></a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped>
header {
  background-color: #0e0e0e;
  color: white;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  z-index: 100;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  padding-left: 7vw;
  padding-right: 7vw;
}


.logo img {
  height: 40px;
}


.nav-menu {
  display: flex;
  align-items: center;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}


.nav-menu a {
  color: white;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.9rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}


.nav-menu a:hover,
.nav-menu a:focus {
  text-decoration: underline;
}


.nav-menu img {
  height: 20px;
  width: auto;
  padding-left: 0.5rem;
}
</style>
