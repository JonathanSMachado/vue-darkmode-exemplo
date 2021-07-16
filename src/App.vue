<template>
  <div class="container" :class="dark ? 'dark' : 'light'">
    <topbar :dark="dark"/>
    <dark-mode-toggle :dark="dark" @toggleDarkMode="toggleDarkMode()"/>
    <main-content />
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'
import Topbar from './components/Topbar.vue';
import DarkModeToggle from './components/DarkModeToggle.vue';
import MainContent from './components/MainContent.vue';

export default {
  name: 'App',
  components: {
    Topbar,
    DarkModeToggle,
    MainContent
  },
  setup() {
    let dark = ref(false);

    function toggleDarkMode() {
      dark.value = !dark.value;
    }
    
    return {
      dark,
      toggleDarkMode
    };
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;700&display=swap');

:root {
  --bg-header-default: #f7f7f7;
  --bg-header-dark: rgb(53, 53, 53);
  --color-header-default: rgb(53, 53, 53);
  --color-header-dark: #f7f7f7;
  --bg-body-default: #fff;
  --bg-body-dark: rgb(32, 32, 32);
  --color-body-default: rgb(32, 32, 32);
  --color-body-dark: #fff;

  --bg-header: var(--bg-header-default);
  --color-header: var(--color-header-default);
  --bg-body: var(--bg-body-default);
  --color-body: var(--color-body-default);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

.container {
  width: 100vw;
  min-height: 100vh;
  background-color: var(--bg-body);
  transition: background-color ease .25s;
}

.container p {
  color: var(--color-body);
}

.container.dark {
  --bg-header: var(--bg-header-dark);
  --color-header: var(--color-header-dark);
  --bg-body: var(--bg-body-dark);
  --color-body: var(--color-body-dark);
}
</style>
