<template>
  <header class="site-header">
    <nav class="nav container" aria-label="Main navigation">
      <div class="brand">SulTech <span class="accent">Solutions</span></div>
      <button
        id="nav-toggle"
        class="nav-toggle"
        :aria-expanded="navOpen"
        @click="toggleNav"
      >
        ☰
      </button>

      <ul id="nav-links" class="nav-links" :class="{ active: navOpen }">
        <li><a href="#home">Home</a></li>
        <li class="dropdown">
          <a href="#" class="dropdown-btn">
            Services <span class="arrow">▾</span>
          </a>
          <ul class="dropdown-menu">
            <li class="dropdown-submenu">
              <button class="submenu-btn" @click="toggleSubmenu">
                Data Services ▸
              </button>
              <ul class="submenu" :style="{ display: submenuOpen ? 'block' : 'none' }">
                <li><a href="#" target="_blank">Data Entry</a></li>
                <li><a href="#" target="_blank">Data Analysis</a></li>
                <li><a href="#" target="_blank">Data Annotation</a></li>
                <li><a href="#" target="_blank">Transcribe</a></li>
              </ul>
            </li>
            <li><a href="#" target="_blank">IT Support</a></li>
            <li><a href="#" target="_blank">Graphics Design</a></li>
            <li><a href="#" target="_blank">Web Development</a></li>
            <li><a href="#" target="_blank">E-Commerce</a></li>
            <li><a href="#" target="_blank">Customer Support</a></li>
            <li><a href="#" target="_blank">Others</a></li>
          </ul>
        </li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#booking">Book</a></li>
        <li><a href="#reviews">Reviews</a></li>
      </ul>

      <div class="nav-actions">
        <button class="btn btn-outline" id="dark-mode-toggle" @click="toggleDark">
          {{ darkMode ? "☀️" : "🌙" }}
        </button>
        <a class="btn btn-primary" href="#booking">Work with Us</a>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      navOpen: false,
      submenuOpen: false,
      darkMode: false,
    };
  },
  methods: {
    toggleNav() {
      this.navOpen = !this.navOpen;
    },
    toggleSubmenu() {
      this.submenuOpen = !this.submenuOpen;
    },
    toggleDark() {
      this.darkMode = !this.darkMode;
      document.body.classList.toggle("dark-mode", this.darkMode);
    },
  },
};
</script>
