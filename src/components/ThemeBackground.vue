<template>
  <CatApi />
</template>

<script>
import CatApi from "./CatApi";
export default {
  components: {
    CatApi,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;300;400;500;700&display=swap");
body {
  background-color: #e7e0c9;
  font-family: "Montserrat", sans-serif;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-items: center;
}
</style>
