<script setup>
import { ref, computed } from 'vue'
import Home from './Home.vue'
import About from './About.vue'
import Contact from './Contact.vue'
import Portfolio from './Portfolio.vue'
import './styles.css';

const routes = {
  '/': Home,
  '/about': About,
  '/contact': Contact,
  '/portfolio': Portfolio
}

const currentRoute = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentRoute.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentRoute.value.slice(1)] || Home
})
</script>

<template>
  <div id="app">
    <header>
      <h1>Hannah Saunders</h1>
    </header>

    <nav>
      <a href="#/">Home</a>
      <a href="#/about">About</a>
      <a href="#/portfolio">Portfolio</a>
      <a href="#/contact">Contact</a>
    </nav>

    <div class="main">
      <component :is="currentView" />
    </div>

<footer class="footer">
  <div class="footer-content">
    <p>© 2026 Hannah Saunders</p>

    <a
      href="https://www.linkedin.com/in/hannah-saunders-1a709234b/"
      target="_blank"
      rel="noopener noreferrer"
      class="linkedin-icon"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="26"
        height="26"
        viewBox="0 0 24 24"
        fill="currentColor"
      >
        <path d="M4.98 3.5C4.98 4.88 3.86 6 2.5 6S0 4.88 0 3.5 1.12 1 2.5 1 4.98 2.12 4.98 3.5zM.22 8.5h4.56V24H.22V8.5zM8.34 8.5h4.37v2.1h.06c.61-1.15 2.1-2.37 4.32-2.37 4.62 0 5.47 3.04 5.47 6.99V24h-4.56v-7.73c0-1.84-.03-4.21-2.57-4.21-2.57 0-2.96 2.01-2.96 4.08V24H8.34V8.5z"/>
      </svg>
    </a>
  </div>
</footer>



  </div>
</template>


<style>
body {
    background-color:#008b8b;
    font-family: Arial;
    margin: 0;
    padding: 0;
}


#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

header {
    background-color:#0b6262;
}

.main {
  flex: 1; /* pushes footer down */
}

nav {
  background-color: #333333;
  display: flex;
  justify-content: center;   /* centers the links horizontally */
  gap: 20px;                 /* space between links */
  padding: 0;
}

nav a {
  color: white;
  text-decoration: none;
  padding: 14px 16px;
}

nav a:hover {
  background-color: #111111;
  padding: 14px 16px;
}

.footer {
  background-color: #333333;
  padding: 20px;
  text-align: center;
}

.footer-content {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px; /* space between text and icon */
}

.footer-content p {
  color: #ffffff;
  margin: 0;
}

.linkedin-icon {
  color: #ffffff;
  transition: opacity 0.2s ease;
}

.linkedin-icon:hover {
  opacity: 0.7;
}

</style>