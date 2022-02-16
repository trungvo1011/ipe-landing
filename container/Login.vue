<template>
  <div
    class="modal moda-login"
    v-bind:class="{ 'is-active': modalLogin }"
    style="animation: fadein 0.5s"
  >
    <SignUp
      v-if="!modalSigin && modalSignup"
      v-bind:modalSignup="modalSignup"
      v-on:changeModalLogin="changeModalLogin"
      v-on:changeModalSignUp="changeModalSignUp"
    />
    <ResetPassword
      v-bind:modalResetPass="modalResetPass"
      v-on:changeModalLogin="changeModalLogin"
      v-on:closeModalResetPassword="closeModalResetPassword"
    />
    <div
      class="modal-background"
      :style="[modalSignup && { backgroundColor: '#0a0a0a1a' }]"
    ></div>
    <div
      class="modal-content"
      v-bind:style="[
        modalSignup || modalResetPass
          ? { display: 'none' }
          : { display: 'block' },
      ]"
    >
      <button
        class="modal-close is-large"
        aria-label="close"
        v-on:click="changeModalLogin"
      ></button>
      <div class="logo">
        <img :src="logo" alt="../assets/images/ipedit.svg" />
      </div>

      <p class="signup-title">로그인</p>
      <!-- Input username -->
      <div class="field">
        <Input
          style="height: 52px"
          className="input"
          type="text"
          name="username"
          placeHolder="이메일"
          :vModel="data.username"
          :checkConditional="checkConditional"
          v-on:handleChange="handleValue"
        />
      </div>

      <!-- Input password -->
      <div class="field">
        <Input
          style="height: 52px"
          className="input"
          type="password"
          name="passwordLogin"
          placeHolder="비밀번호"
          :vModel="data.password"
          :checkConditional="checkConditional"
          v-on:handleChange="handleValue"
        />
      </div>

      <!-- Remember password -->
      <div class="checkbox-control">
        <label class="container__checbox"
          >이메일 저장하기
          <input type="checkbox" checked="checked" @change="someHandler" />
          <span
            class="checkmark"
            :class="{ checkmark__active: typeCheckbox }"
          ></span>
        </label>
        <a class="forget-pass" v-on:click="openModalResetPassword"
          >비밀번호 찾기</a
        >
      </div>

      <!-- login with Email -->

      <Button
        style="width: 100%"
        :style="[
          data.userName !== '' &&
            data.password !== '' && {
              background: '#5C6BC0',
              color: '#fff',
            },
        ]"
        text="로그인"
      >
        로그인
      </Button>

      <p class="or">또는</p>

      <!-- login with Goolge -->
      <div class="field">
        <img :src="google" alt="" style="position: absolute" />
        <p class="control">
          <button class="button google">Google로 로그인하기</button>
        </p>
      </div>

      <!-- login with apple -->
      <div class="field">
        <img :src="apple" alt="" style="position: absolute" />
        <p class="control">
          <button class="button apple">Apple로 로그인하기</button>
        </p>
      </div>

      <p class="signup">
        IPEDIT이 처음이신가요?<span v-on:click="openModalSignUp">회원가입</span>
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/login.scss";
</style>

<script>
import SignUp from "./SignUp.vue";
import ResetPassword from "./ResetPassword.vue";
import Logo from "../assets/images/ipedit.svg";
import Google from "../assets/images/google.svg";
import Apple from "../assets/images/apple.svg";
import Input from "../components/Inputs.vue";
export default {
  data() {
    return {
      modalSignup: false,
      modalSigin: false,
      logo: Logo,
      google: Google,
      apple: Apple,
      checkConditional: false,
      modalResetPass: false,
      typeCheckbox: true,
      data: { userName: "", password: "" },
    };
  },
  props: {
    modalLogin: Boolean,
  },
  components: { SignUp, ResetPassword, Input },
  methods: {
    changeModalLogin: function () {
      this.$emit("changeModalLogin");
    },
    changeModalSignUp: function () {
      this.modalSignup = false;
    },
    openModalSignUp: function () {
      this.modalSignup = true;
    },
    handleValue: function (e) {
      this.checkConditional = true;
      this.data = { [e.target.name]: e.target.value };
    },
    openModalResetPassword: function () {
      document.querySelector("html").classList.add("is-clipped");
      this.modalResetPass = true;
    },
    closeModalResetPassword: function () {
      document.querySelector("html").classList.remove("is-clipped");
      this.modalResetPass = false;
    },
    someHandler: function (e) {
      this.typeCheckbox = e.target.checked;
    },
  },
  created() {
    if (typeof window !== "undefined") {
      window.addEventListener("keydown", (evt) => {
        evt = evt || window.event;
        if (evt.keyCode == 27) {
          this.$emit("changeModalLogin");
        }
      });
    }
  },
};
</script>
