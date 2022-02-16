<template>
  <!-- v-bind:class="{ 'is-active': modalSignup }" -->
  <div class="modal sign-up is-active">
    <div
      class="modal-background"
      :style="[modalLogin && { backgroundColor: '#0a0a0a0d ' }]"
    ></div>
    <SignUpEmail
      v-if="signupEmail"
      v-on:changeModalSignUp="changeModalSignUp"
    />
    <div class="modal-content" v-if="!signupEmail">
      <button
        class="modal-close is-large"
        aria-label="close"
        v-on:click="changeModalSignUp"
      ></button>
      <div class="logo">
        <img :src="logo" alt="../assets/images/ipedit.svg" />
      </div>

      <p class="signup-title">회원가입</p>

      <!-- login with Email -->
      <Button
        style="width: 100%"
        v-on:click="signupEmail = !signupEmail"
        text="이메일로 가입하기"
      >
      </Button>

      <p class="or">또는</p>

      <!-- login with Goolge -->
      <div class="field" style="margin-bottom: 12px">
        <img :src="google" alt="" style="position: absolute; left: 16px" />
        <p class="control">
          <!-- <button class="button google"></button> -->
          <Button class="google" text="Google로 시작하기"> </Button>
        </p>
      </div>

      <!-- login with apple -->
      <div class="field" style="margin-bottom: 12px">
        <img :src="apple" alt="" style="position: absolute; left: 16px" />
        <p class="control">
          <Button class="apple" text="Apple로 시작하기"> </Button>
          <!-- <button class="button apple">Apple로 시작하기</button> -->
        </p>
      </div>

      <p class="signup">
        이미 회원이신가요?<span v-on:click="openModalLogin">로그인</span>
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/signUp.scss";
</style>

<script>
import Logo from "../assets/images/ipedit.svg";
import Google from "../assets/images/google.svg";
import Apple from "../assets/images/apple.svg";

import SignUpEmail from "./SignupEmail.vue";
export default {
  data() {
    return {
      signupEmail: false,
      logo: Logo,
      google: Google,
      apple: Apple,
      loginFrUp: false,
    };
  },
  props: {
    modalSignup: Boolean,
    modalLogin: Boolean,
  },
  components: { SignUpEmail },
  methods: {
    changeModalSignUp: function () {
      this.$emit("changeModalLogin");
      this.$emit("changeModalSignUp");
    },
    openModalLogin: function () {
      this.$emit("changeModalSignUp");
      this.$emit("openModalLogin");
    },
  },
  created() {
    if (typeof window !== "undefined") {
      window.addEventListener("keydown", (evt) => {
        evt = evt || window.event;
        if (evt.keyCode == 27) {
          this.$emit("changeModalLogin");
          this.$emit("changeModalSignUp");
        }
      });
    }
  },
  mounted() {},
};
</script>
