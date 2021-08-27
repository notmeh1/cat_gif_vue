<template>
  <div id="app">
      <ThemeBackground/>
  </div>
</template>

<script>
import ThemeBackground from './components/ThemeBackground'

export default {
  name: "App",
  components: {
    ThemeBackground
  },
};
</script>

<style>
body {
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
}
</style>
