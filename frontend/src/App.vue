<template>
  <ul>
    <custom-header title="Remember Me"></custom-header>
    <the-resources :storedResources="storedResources"> </the-resources>
  </ul>
</template>

<script>
// import StoredResources from "./components/learning/StoredResources.vue";
import CustomHeader from "./components/layouts/CustomHeader.vue";
import TheResources from "./components/learning/TheResources.vue";
export default {
  components: {
    TheResources,
    CustomHeader,
  },
};
</script>

<!-- if u want to keep the design only local to this component use scoped prop -->
<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>
