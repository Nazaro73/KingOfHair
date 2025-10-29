<template>
  <nav class="nav-menu" :class="{ scrolled: isScrolled }">
    <div class="nav-container">
      <div class="nav-logo">
        <img src="@/assets/logo-kingofhair.png" alt="King of Hair" class="logo-img" />
      </div>

      <button class="nav-toggle" @click="toggleMenu" :aria-label="isMenuOpen ? 'Fermer le menu' : 'Ouvrir le menu'">
        <span class="hamburger" :class="{ active: isMenuOpen }"></span>
      </button>

      <ul class="nav-links" :class="{ open: isMenuOpen }">
        <li><a href="#accueil" @click="closeMenu">Accueil</a></li>
        <li><a href="#services" @click="closeMenu">Services</a></li>
        <li><a href="#tarifs" @click="closeMenu">Tarifs</a></li>
        <li><a href="#avis" @click="closeMenu">Avis</a></li>
        <li><a href="#actualites" @click="closeMenu">Actualités</a></li>
        <li><a href="#contact" @click="closeMenu">Contact</a></li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.nav-menu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background-color: transparent;
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
}

.nav-menu.scrolled {
  background-color: rgba(33, 33, 33, 0.95);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

.nav-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 15px 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-logo {
  height: 50px;
}

.logo-img {
  height: 100%;
  width: auto;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.5));
}

.nav-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 5px;
  z-index: 1001;
}

.hamburger {
  display: block;
  width: 30px;
  height: 3px;
  background-color: #d1ae5f;
  position: relative;
  transition: all 0.3s ease;
}

.hamburger::before,
.hamburger::after {
  content: '';
  position: absolute;
  width: 30px;
  height: 3px;
  background-color: #d1ae5f;
  transition: all 0.3s ease;
}

.hamburger::before {
  top: -10px;
}

.hamburger::after {
  top: 10px;
}

.hamburger.active {
  background-color: transparent;
}

.hamburger.active::before {
  top: 0;
  transform: rotate(45deg);
}

.hamburger.active::after {
  top: 0;
  transform: rotate(-45deg);
}

.nav-links {
  display: flex;
  gap: 40px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-links li a {
  color: #FFFFFF;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 500;
  transition: color 0.3s ease;
  position: relative;
}

.nav-links li a::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background-color: #d1ae5f;
  transition: width 0.3s ease;
}

.nav-links li a:hover {
  color: #d1ae5f;
}

.nav-links li a:hover::after {
  width: 100%;
}

@media (max-width: 768px) {
  .nav-container {
    padding: 15px 20px;
  }

  .nav-logo {
    height: 40px;
  }

  .nav-toggle {
    display: block;
  }

  .nav-links {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    height: 100vh;
    background-color: rgba(33, 33, 33, 0.98);
    flex-direction: column;
    gap: 0;
    padding: 100px 30px 30px;
    transition: right 0.3s ease;
    box-shadow: -5px 0 15px rgba(0, 0, 0, 0.3);
  }

  .nav-links.open {
    right: 0;
  }

  .nav-links li {
    padding: 20px 0;
    border-bottom: 1px solid rgba(209, 174, 95, 0.2);
  }

  .nav-links li:last-child {
    border-bottom: none;
  }

  .nav-links li a {
    font-size: 1.3rem;
  }
}
</style>
