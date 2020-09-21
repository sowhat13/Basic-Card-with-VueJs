<template>
  <div id="app">
    <superpeer-card></superpeer-card>
  </div>
</template>

<script>
import SuperpeerCard from "./components/SuperpeerCard";

export default {
  name: "app",
  components: {
    SuperpeerCard
  }
};
</script>

<style lang="scss">
//variables
@import "./assets/scssvariables.scss";

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: $base-font;
  background: $grey-10;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 100%;
}
</style>
