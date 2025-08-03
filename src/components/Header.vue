<template>
  <header :dir="isRTL ? 'rtl' : 'ltr'">
    <nav role="navigation" aria-label="Main navigation">
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

      <div
          class="hamburger"
          @click="toggleMenu"
          role="button"
          aria-label="Open menu"
          tabindex="0"
          @keyup.enter="toggleMenu"
      >
        <img src="../../src/assets/Menu-White.svg" alt="Menu Icon" />
      </div>
    </nav>

    <!-- Drawer Menu -->
    <div
        class="drawer"
        :class="{ active: menuOpen }"
        role="dialog"
        aria-modal="true"
    >
      <div
          class="close-icon"
          @click="toggleMenu"
          role="button"
          aria-label="Close menu"
          tabindex="0"
          @keyup.enter="toggleMenu"
      >
        <img src="../../src/assets/Close White.svg" alt="Close Icon" />
      </div>
      <ul class="drawer-menu">
        <li v-for="(item, index) in drawerMenuItems" :key="index">
          <a href="#" tabindex="0">{{ item }}</a>
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
        return this.menuItems.slice(3, 5); // tablet
      } else {
        return this.menuItems; // mobile
      }
    },
    isRTL() {
      // Change to dynamic detection if needed (e.g., locale === 'ar')
      return false;
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
  beforeUnmount() {
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
  transition: color 0.3s, transform 0.3s;
}
.nav-menu a:hover,
.nav-menu a:focus {
  color: #f89603;
  transform: translateY(-2px);
}


.hamburger {
  display: none;
  cursor: pointer;
}


.drawer {
  position: fixed;
  top: 0;
  right: 0;
  width: 250px;
  height: 100vh;
  background-color: #0e0e0e;
  transform: translateX(100%);
  transition: transform 0.4s ease-in-out;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 4rem;
  z-index: 2000;
}
.drawer.active {
  transform: translateX(0);
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
  transition: color 0.3s ease, transform 0.3s ease;
}
.drawer-menu a:hover,
.drawer-menu a:focus {
  color: #f89603;
  transform: translateX(5px);
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
  animation: fadeIn 0.3s ease-in-out forwards;
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* RTL layout support */
:host([dir="rtl"]) nav {
  direction: rtl;
  flex-direction: row-reverse;
}
:host([dir="rtl"]) .drawer {
  right: auto;
  left: 0;
  transform: translateX(-100%);
}
:host([dir="rtl"]) .drawer.active {
  transform: translateX(0);
}
:host([dir="rtl"]) .close-icon {
  right: auto;
  left: 2vw;
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
