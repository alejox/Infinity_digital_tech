<template>
  <main>
    <router-view />
  </main>
</template>

<script>

export default {
  name: "App",

  data: () => ({
    //
  }),
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 62.5%;
}

body {
  font-family: "Jost", sans-serif;
}
</style>
