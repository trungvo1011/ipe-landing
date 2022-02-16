<template>
  <button class="button btn">{{ text }}</button>
</template>

<style lang="scss" scoped>
// @import "../assets/stylesheets/login.scss";
@import "../assets/stylesheets/signUp.scss";
</style>

<script>
export default {
  data() {
    return {
      tempPassword: "",
    };
  },
  props: {
    text: String,
    disabled: Boolean,
  },
  components: {},
  methods: {},
};
</script>
