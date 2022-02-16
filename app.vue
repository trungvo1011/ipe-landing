<template>
  <NuxtPage id="__layout" style="background: #f6f7f9" />
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
