<template>
  <div id="app">
    <Header/>
    <DiscList/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import DiscList from "./components/DiscList.vue";

export default {
  name: "App",
  components: {
    Header,
    DiscList,
  },
};
</script>

<style lang="scss">
@import './style/general.scss';
</style>
