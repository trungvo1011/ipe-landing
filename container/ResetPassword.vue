<template>
  <div class="modal" v-bind:class="{ 'is-active': modalResetPass }">
    <SuccessPopup
      v-bind:successPopup="successPopup"
      v-on:closeModalSuccess="closeModalSuccess"
      v-on:changeModalLogin="changeModalLogin"
      v-on:closeModalResetPassword="closeModalResetPassword"
      v-on:closeModalReset="closeModalReset"
    />
    <!-- <div class="modal-background is-clipped"></div> -->
    <div class="modal-content" v-if="!sendEmail && !successPopup">
      <button
        class="modal-close is-large"
        aria-label="close"
        v-on:click="closeModalReset"
      ></button>

      <h1>비밀번호 찾기</h1>
      <p class="">
        가입 시 등록하신 이메일을 입력하세요.<br />
        비밀번호 재설정 이메일을 보내드립니다.
      </p>
      <!-- Input username -->
      <div class="field">
        <Input
          style="height: 48px"
          className="input"
          type="text"
          name="emailReset"
          placeHolder="이메일 주소"
          :vModel="data.emailReset"
          :checkConditional="checkConditional"
          v-on:handleChange="handleValue"
        />
      </div>

      <!-- Reset -->
      <Button
        :class="[data.emailReset === '' && 'disable btn-reset']"
        text="이메일 받기"
        v-on:click="onToogleEmail"
      >
      </Button>
    </div>

    <!-- NewPassword -->
    <div
      class="modal-content"
      style="height: 315px"
      v-if="sendEmail && !successPopup"
    >
      <button
        class="modal-close is-large"
        aria-label="close"
        v-on:click="closeModalReset"
      ></button>

      <h1>새로운 비밀번호</h1>
      <p class="">새로운 비밀번호를 입력해주세요.</p>
      <!-- Input old Pass -->
      <div class="field" style="margin-bottom: 12px">
        <Input
          style="height: 48px"
          className="input"
          type="password"
          name="oldPassReset"
          placeHolder="비밀번호"
          :vModel="data.oldPassReset"
          :checkConditional="checkConditional"
          v-on:handleChange="handleValue"
        />
      </div>

      <!-- Input new Pass -->
      <div class="field">
        <Input
          style="height: 48px"
          className="input"
          type="password"
          name="newPassReset"
          placeHolder="비밀번호 재입력"
          :vModel="data.newPassReset"
          :checkConditional="checkConditional"
          v-on:handleChange="handleValue"
        />
      </div>

      <!-- Reset -->
      <Button
        :class="[
          data.newPassReset === '' &&
            data.oldPassReset === '' &&
            'disable btn-reset',
        ]"
        text="이메일 받기"
        v-on:click="openResult"
      >
      </Button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/login.scss";
@import "../assets/stylesheets/resetPassword.scss";
</style>

<script>
import Input from "../components/Inputs.vue";
import SuccessPopup from "../components/SuccessPopup.vue";
export default {
  data() {
    return {
      data: { emailReset: "", oldPassReset: "", newPassReset: "" },
      checkConditional: false,
      sendEmail: false,
      successPopup: false,
    };
  },
  props: { modalResetPass: Boolean },
  components: { Input, SuccessPopup },
  methods: {
    closeModalReset: function () {
      this.$emit("closeModalResetPassword");
      this.$emit("changeModalLogin");
    },
    closeModalSuccess: function () {
      this.successPopup = false;
      this.$emit("closeModalResetPassword");
    },
    handleValue: function (e) {
      this.checkConditional = true;
      this.data = { [e.target.name]: e.target.value };
    },
    openResult: function () {
      // this.$emit("closeModalResetPassword");
      this.successPopup = true;
      this.sendEmail = false;
    },
    onToogleEmail: function () {
      if (this.data.emailReset !== "") {
        this.sendEmail = true;
      }
    },
  },
  mounted() {},
  created() {
    if (typeof window !== "undefined") {
      window.addEventListener("keydown", (evt) => {
        evt = evt || window.event;
        if (evt.keyCode == 27) {
          this.$emit("closeModalResetPassword");
        }
      });
    }
  },
};
</script>
