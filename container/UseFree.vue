<template>
  <div class="useFree">
    <div class="useFree__container containerr">
      <div class="h1">
        <img :src="Translate" alt="Translate" />
        <h1>
          <span>번역에 필요한 모든 고민을 대신 해드립니다.</span>
          <span>특허 명세서 번역 전용 에디터</span>
        </h1>
      </div>
      <!-- <a class="button btn btn-useFree"> </a> -->
      <div class="div_btn">
        <Button
          class="btn-useFree"
          v-on:click="openModalSignUp"
          text="바로가기"
        >
        </Button>
      </div>
    </div>
    <Login
      v-if="modalLogin"
      v-bind:modalLogin="modalLogin"
      v-on:changeModalLogin="changeModalLogin"
    />
    <SignUp
      v-if="modalSignup"
      v-bind:modalSignup="modalSignup"
      v-on:changeModalSignUp="changeModalSignUp"
      v-on:openModalLogin="openModalLogin"
      v-on:changeModalLogin="changeModalLogin"
    />
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/useFree.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script>
import SignUp from "./SignUp.vue";
import Login from "./Login.vue";
import Translate from "../assets/images/translate.svg";
export default {
  data() {
    return {
      Translate: Translate,
      modalLogin: false,
      modalSignup: false,
      modalSigin: false,
      loginFree: false,
    };
  },
  components: { SignUp, Login },
  methods: {
    changeModalSignUp: function () {
      document.querySelector("html").classList.remove("is-clipped");
      this.modalSignup = false;
    },
    openModalSignUp: function () {
      document.querySelector("html").classList.add("is-clipped");
      this.modalSignup = true;
    },
    openModalLogin: function () {
      this.modalLogin = true;
    },
    changeModalLogin: function () {
      this.modalLogin = false;
    },
  },
};
</script>
