<template>
  <div class="toggle-container" :class="dark ? 'dark' : 'light'">
    <label class="toggle">
      <input type="checkbox" :checked="dark" @change="emit('toggleDarkMode')">
      <span class="toggler"></span>
    </label>
    <span>Switch mode</span>
  </div>
</template>

<script>
export default {
  props: {
    dark: {
      type: Boolean
    }
  },

  setup(props, { emit }) {
    return {
      emit
    };
  }
}
</script>

<style scoped>
:root {
  --ligh-opacity: 1;
  --dark-opacity: 1;
}

.toggle-container {
  position: fixed;
  bottom: 15px;
  left: 15px;
  display: flex;
  align-items: center;
}

.toggle-container > span {
  margin-left: 10px;
}

.toggle-container > span::before {
  content: '<<';
  padding-right: 5px;
}

.toggle-container.light > span {
  color: #333;
}

.toggle-container.dark > span {
  color: #f1f1f1;
}

.toggle {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #5a5a5a;
  height: 32px;
  width: 60px;
  border-radius: 32px;
}

.toggle::before, .toggle::after {
  font-size: 18px;
  transition: opacity ease .25s;
}

.toggle::after {
  content: "🌜";
  padding-right: 6px;
  opacity: var(--dark-opacity);
}

.toggle::before {
  content: "🌞";
  padding-left: 6px;
  opacity: var(--light-opacity);
}

.toggler {
  border: 2px solid gold;
  border-radius: 50%;
  width: 27px;
  height: 27px;
  position: absolute;
  text-indent: -999em;
  transition: transform 0.25s;
  margin: 3px;
  box-shadow: 0 0 6px 1px goldenrod;
}

.toggle > input {
  opacity: 0;
  position: absolute;
  top: -999em;
}

.toggle > input:checked ~ .toggler {
  transform: translateX(100%);
}

.toggle-container.light {
  --light-opacity: 1;
  --dark-opacity: 0.5;
}

.toggle-container.dark {
  --light-opacity: 0.5;
  --dark-opacity: 1;
}

</style>