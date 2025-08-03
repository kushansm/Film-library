<template>
  <header>
    <nav>
      <div class="logo">
        <img src="../../src/assets/Logo White.svg" alt="Logo" />
      </div>

      <ul class="nav-menu">
        <li class="show-on-all"><a href="#">HOME</a></li>
        <li class="show-on-all"><a href="#">OUR SCREENS</a></li>
        <li class="show-on-all"><a href="#">SCHEDULE</a></li>
        <li class="hide-on-md"><a href="#">MOVIE LIBRARY</a></li>
        <li class="hide-on-md"><a href="#">LOCATION & CONTACT</a></li>
      </ul>

      <div class="hamburger" @click="toggleMenu">
        <img src="../../src/assets/Menu-White.svg" alt="Menu Icon" />
      </div>
    </nav>

    <!-- Overlay Menu Drawer -->
    <div class="drawer" :class="{ active: menuOpen }">
      <div class="close-icon" @click="toggleMenu">
        <img src="../../src/assets/Close White.svg" alt="Close Icon" />
      </div>
      <ul class="drawer-menu">
        <li v-for="(item, index) in drawerMenuItems" :key="index">
          <a href="#">{{ item }}</a>
        </li>
      </ul>
    </div>

    <!-- Backdrop Overlay -->
    <div class="overlay" v-if="menuOpen" @click="toggleMenu"></div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      menuOpen: false,
      windowWidth: window.innerWidth,
      menuItems: [
        "HOME",
        "OUR SCREENS",
        "SCHEDULE",
        "MOVIE LIBRARY",
        "LOCATION & CONTACT",
      ],
    };
  },
  computed: {
    drawerMenuItems() {
      if (this.windowWidth >= 768 && this.windowWidth < 1024) {
        // Tablet View — Show only the hidden items in drawer
        return this.menuItems.slice(3, 5);
      } else {
        // Mobile View — Show all items in drawer
        return this.menuItems;
      }
    },
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    updateWindowWidth() {
      this.windowWidth = window.innerWidth;
    },
  },
  mounted() {
    window.addEventListener("resize", this.updateWindowWidth);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.updateWindowWidth);
  },
};
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
  z-index: 1000;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  padding-left: 7vw;
  padding-right: 7vw;
  height: 70px;
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

/* Hamburger Icon */
.hamburger {
  display: none;
  cursor: pointer;
}

/* Drawer Menu */
.drawer {
  position: fixed;
  top: 0;
  right: -300px;
  width: 250px;
  height: 100vh;
  background-color: #0e0e0e;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 4rem;
  transition: right 0.4s ease-in-out;
  z-index: 2000;
}

.drawer.active {
  right: 0;
}

.drawer-menu {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.drawer-menu a {
  color: white;
  font-size: 1.2rem;
  text-decoration: none;
}

.close-icon {
  position: absolute;

  top: 2vh;
  right: 2vw;
  cursor: pointer;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1500;
}

@media (min-width: 1024px) {
  .hide-on-md {
    display: inline;
  }
  .hamburger {
    display: none;
  }
}

@media (min-width: 768px) and (max-width: 1023px) {
  .hide-on-md {
    display: none;
  }
  .hamburger {
    display: block;
  }
  .nav-menu {
    display: flex;
  }
}

@media (max-width: 767px) {
  .nav-menu {
    display: none;
  }
  .hamburger {
    display: block;
  }
}
</style>