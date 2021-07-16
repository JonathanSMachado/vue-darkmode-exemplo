<template>
  <header class="header">
    <h2>{{ dark ? 'dark mode' : 'light mode' }}</h2>
    <nav class="navbar">
      <ul>
        <li><a href="">About</a></li>
        <li><a href="">Projects</a></li>
        <li><a href="">Contact</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  props: {
    dark: {
      type: Boolean
    }
  }
}
</script>

<style scoped>
  * {
    color: var(--color-header);
    text-transform: uppercase;
    letter-spacing: 2px;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-content: center;
    padding: 35px;
    background-color: var(--bg-header);
    transition: background-color ease .25s;
  }

  .header h2 {
    margin: auto 0;
  }

  .navbar ul {
    display: flex;
    list-style: none;
  }

  .navbar ul li {
    padding: 15px;
    transition: background-color ease .25s;
  }

  .navbar ul li:hover {
    background-color: lightskyblue;
  }

  .navbar ul li:hover a {
    color: #333;
  }

  .navbar a {
    text-decoration: none;
  }
</style>