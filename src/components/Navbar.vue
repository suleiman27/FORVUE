<template>
  <header class="site-header">
    <nav class="nav container" aria-label="Main navigation">
      <div class="brand">SulTech <span class="accent">Solutions</span></div>

      <button
        class="nav-toggle"
        :aria-expanded="navOpen"
        @click="toggleNav"
      >
        ☰
      </button>

      <ul class="nav-links" :class="{ active: navOpen }">
        <li><a href="#home" @click="closeNav">Home</a></li>

        <li class="dropdown">
          <a href="#" class="dropdown-btn" @click.prevent="toggleSubmenu">
            Services <span class="arrow">▾</span>
          </a>

          <ul class="dropdown-menu" :class="{ active: submenuOpen }">
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

        <li><a href="#gallery" @click="closeNav">Gallery</a></li>
        <li><a href="#about" @click="closeNav">About</a></li>
        <li><a href="#booking" @click="closeNav">Book</a></li>
        <li><a href="#reviews" @click="closeNav">Reviews</a></li>
      </ul>

      <div class="nav-action
