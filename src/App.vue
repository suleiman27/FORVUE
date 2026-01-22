<template>
  <div :class="{ 'dark-mode': darkMode }">
    <!-- HEADER / NAV -->
    <header class="site-header">
      <nav class="nav container" aria-label="Main navigation">
        <div class="brand">SulTech <span class="accent">Solutions</span></div>

        <button id="nav-toggle" class="nav-toggle" aria-expanded="false"
                aria-controls="nav-links" aria-label="Toggle navigation"
                @click="toggleNav">
          ☰
        </button>

        <ul id="nav-links" class="nav-links" :class="{ active: navOpen }">
          <li><router-link to="/">Home</router-link></li>

          <!-- SERVICES DROPDOWN -->
          <li class="dropdown">
            <a href="#" class="dropdown-btn">Services <span class="arrow">▾</span></a>
            <ul class="dropdown-menu">
              <li class="dropdown-submenu">
                <button class="submenu-btn" @click="toggleSubmenu">
                  Data Services ▸
                </button>
                <ul class="submenu" v-show="submenuOpen">
                  <li><a href="services-pages/data-entry/data-entry.html" target="_blank">Data Entry</a></li>
                  <li><a href="services-pages/data-analysis/data-analysis.html" target="_blank">Data Analysis</a></li>
                  <li><a href="services-pages/data-annotation/data-annotation.html" target="_blank">Data Annotation</a></li>
                  <li><a href="services-pages/transcribe/transcribe.html" target="_blank">Transcribe</a></li>
                </ul>
              </li>

              <li><a href="services-pages/it-support/it-support.html" target="_blank">IT Support</a></li>
              <li><a href="services-pages/graphics-design/graphics-design.html" target="_blank">Graphics Design</a></li>
              <li><a href="services-pages/web-development/web-development.html" target="_blank">Web Development</a></li>
              <li><a href="services-pages/e-commerce/e-commerce.html" target="_blank">E-Commerce</a></li>
              <li><a href="services-pages/data-services/data-services.html" target="_blank">Data Services</a></li>
              <li><a href="services-pages/others/others.html" target="_blank">Others</a></li>
            </ul>
          </li>

          <li><router-link to="/gallery">Gallery</router-link></li>
          <li><router-link to="/about">About</router-link></li>
          <li><router-link to="/booking">Book</router-link></li>
          <li><router-link to="/reviews">Reviews</router-link></li>
        </ul>

        <div class="nav-actions">
          <button class="btn btn-outline" id="dark-mode-toggle"
                  @click="toggleDarkMode">
            {{ darkMode ? "☀️" : "🌙" }}
          </button>
          <router-link class="btn btn-primary" to="/booking">Work with Us</router-link>
        </div>
      </nav>
    </header>

    <!-- MAIN CONTENT -->
    <router-view />

    <!-- FOOTER -->
    <footer class="site-footer">
      <div class="container">
        <div>© {{ currentYear }} SulTech Solutions</div>
        <div><a href="mailto:info@sultech.com">info@sultech.com</a> • +254 708189577</div>
      </div>
    </footer>

    <!-- WHATSAPP FLOATING BUTTON -->
    <a href="https://api.whatsapp.com/send?phone=254708189577&text=Hello%20SulTech%20Solutions,%20I%20need%20your%20services"
       class="float" target="_blank">
      <i class="fa fa-whatsapp my-float"></i>
    </a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSlide: 0,
      navOpen: false,
      submenuOpen: false,
      darkMode: false,
      slides: [
        "images/BACKGROUND.jpg",
        "images/OUTSOURCING.jpg",
        "images/OUTSOURCING1.jpg"
      ]
    };
  },
  computed: {
    currentYear() {
      return new Date().getFullYear();
    }
  },
  mounted() {
    setInterval(() => {
      this.currentSlide = (this.currentSlide + 1) % this.slides.length;
    }, 4000);
  },
  methods: {
    toggleNav() {
      this.navOpen = !this.navOpen;
    },
    toggleSubmenu() {
      this.submenuOpen = !this.submenuOpen;
    },
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
    }
  }
};
</script>

<style scoped>
/* ========================
   RESET & BASE
======================== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Arial', sans-serif;
}

body {
  background-color: #fff;
  color: #222;
  line-height: 1.6;
  transition: background 0.3s, color 0.3s;
}

a {
  text-decoration: none;
  color: inherit;
}

/* ========================
   DARK MODE
======================== */
.dark-mode {
  background-color: #121212;
  color: #ddd;
}

.dark-mode .site-header {
  background-color: #1e1e1e;
  box-shadow: 0 2px 5px rgba(255,255,255,0.05);
}

.dark-mode .dropdown-menu,
.dark-mode .submenu {
  background-color: #1e1e1e;
}

.dark-mode .site-footer {
  background-color: #1e1e1e;
  color: #ddd;
}

.dark-mode .btn-outline {
  color: #6a0dad;
  border-color: #6a0dad;
}

.dark-mode .btn-primary {
  background-color: #9b59b6;
  color: #fff;
}

.dark-mode .hero-overlay {
  background: rgba(0,0,0,0.5);
}

/* ========================
   HEADER / NAV
======================== */
.site-header {
  width: 100%;
  background: #fff;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  position: fixed;
  top: 0;
  z-index: 1000;
  transition: background 0.3s, box-shadow 0.3s;
}

.nav.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
}

.brand {
  font-size: 1.5rem;
  font-weight: bold;
}

.brand .accent {
  color: #6a0dad;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 1rem;
}

.nav-links li {
  position: relative;
}

.nav-links a {
  padding: 0.5rem 0.7rem;
  font-weight: 500;
}

.nav-links a:hover,
.dropdown-menu a:hover {
  color: #6a0dad;
}

/* Dropdown Menu */
.dropdown-menu,
.submenu {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  background: #fff;
  box-shadow: 0 2px 8px rgba(0,0,0,0.15);
  padding: 0.5rem 0;
  min-width: 180px;
  border-radius: 6px;
  z-index: 1000;
}

.dropdown-menu li {
  padding: 0.3rem 1rem;
}

.dropdown:hover .dropdown-menu {
  display: block;
}

/* Buttons */
.btn {
  padding: 0.5rem 1rem;
  border: none;
  cursor: pointer;
  font-weight: 500;
  border-radius: 6px;
  transition: all 0.3s;
}

.btn-primary {
  background-color: #6a0dad;
  color: #fff;
}

.btn-primary:hover {
  background-color: #7e33d0;
}

.btn-outline {
  border: 2px solid #6a0dad;
  background: transparent;
  color: #6a0dad;
}

.btn-outline:hover {
  background-color: #6a0dad;
  color: #fff;
}

/* ========================
   HERO
======================== */
.hero {
  position: relative;
  height: 500px;
  overflow: hidden;
  margin-top: 70px;
}

.hero-slideshow {
  width: 100%;
  height: 100%;
  position: relative;
}

.hero-slideshow .slide {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

.hero-slideshow .slide.active {
  opacity: 1;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.3);
  transition: background 0.3s;
}

.hero-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  text-align: center;
}

.hero-content h1 {
  font-size: 2rem;
  text-shadow: 1px 1px 6px rgba(0,0,0,0.7);
}

.hero-content .lead {
  margin: 1rem 0;
  font-size: 1.1rem;
}

.ctas .btn {
  margin: 0.5rem;
}

/* ========================
   SERVICES GRID
======================== */
.sultech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.sultech-card {
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  text-align: center;
  overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
}

.sultech-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

.sultech-card img {
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.sultech-card h3 {
  margin: 0.5rem 0;
  color: #6a0dad;
}

/* ========================
   WHY CHOOSE US
======================== */
.choose-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.choose-card {
  background: #f9f9f9;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
}

.choose-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 3px 10px rgba(0,0,0,0.15);
}

/* ========================
   ABOUT
======================== */
.about-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  align-items: center;
  margin-top: 1rem;
}

.about-img {
  flex: 1 1 250px;
  width: 100%;
  height: 250px;
  object-fit: cover;
  border-radius: 6px;
  transition: transform 0.3s;
}

.about-img:hover {
  transform: scale(1.03);
}

/* ========================
   BOOKING FORM
======================== */
.booking-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.booking-form .row.two {
  display: flex;
  gap: 1rem;
}

.booking-form input {
  flex: 1;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 6px;
}

/* ========================
   FOOTER
======================== */
.site-footer {
  background: #222;
  color: #fff;
  padding: 1rem 2rem;
  text-align: center;
}

.site-footer a {
  color: #6a0dad;
}

/* ========================
   WHATSAPP FLOATING BUTTON
======================== */
.float {
  position: fixed;
  width: 60px;
  height: 60px;
  bottom: 20px;
  right: 20px;
  background-color: #25d366;
  color: #fff;
  border-radius: 50px;
  text-align: center;
  font-size: 30px;
  box-shadow: 2px 2px 5px rgba(0,0,0,0.3);
  z-index: 1000;
}

.float:hover {
  background-color: #128c7e;
}

.my-float {
  margin-top: 15px;
}

/* ========================
   RESPONSIVE
======================== */
@media (max-width: 768px) {
  .nav-links {
    flex-direction: column;
    display: none;
  }

  .nav-links.active {
    display: flex;
  }

  .booking-form .row.two {
    flex-direction: column;
  }

  .about-grid {
    flex-direction: column;
  }

  .hero-content h1 {
    font-size: 1.5rem;
  }
}
</style>
