<template>
  <NuxtPage id="__layout" />
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/main.sass";
@import "../assets/stylesheets/global.scss";
</style>;
<script >
import Main from "./pages";

export default {
  data() {
    return {};
  },
  components: {
    Main,
  },
};
</script>
