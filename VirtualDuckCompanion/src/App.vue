<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import MainWelcome from './components/MainWelcome.vue'
import SidePanel from './components/SidePanel.vue'

const isPanelVisible = ref(false)
let label = ref('>')

const togglePanelVisibility = () => {
  isPanelVisible.value = !isPanelVisible.value
  if (isPanelVisible.value) label = '<'
  else label = '>'
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.webp" width="125" height="125" />

    <div class="wrapper">
      <MainWelcome msg="Welcome" />
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/main">Main</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />

  <SidePanel :is-visible="isPanelVisible" />
    <button class="toggle-button" @click="togglePanelVisibility">{{ label }}</button>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
  background-image: url(../src/assets/background.png);
  padding: 2%;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
  border-radius: 50%;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

/* Add your styles here, including styles for .toggle-button */
.toggle-button {
  position: fixed;
  top: 1%;
  left: 0; /* Adjust based on the side panel's width */
  transform: translateY(-50%);
  z-index: 1000; /* Ensure it's above other elements */
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
