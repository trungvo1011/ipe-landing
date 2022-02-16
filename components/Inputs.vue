<template>
  <div style="width: 100%; position: relative; height: max-content">
    <div class="omrs-input-group">
      <label class="omrs-input-filled">
        <input
          class="input"
          required
          :name="name"
          :style="[
            checkConditional &&
              !checkConditionalFunction() && { borderColor: '#d2416d' },
          ]"
          :type="type"
          v-model="vModel"
          v-on:change="handleChange"
        />
        <span class="omrs-input-label">{{ placeHolder }}</span>
      </label>
      <div
        class="control control-button"
        :style="[!buttonRequire ? { display: 'none' } : { display: 'block' }]"
      >
        <button
          :class="{ disable: vModel === '' }"
          :style="[
            vModel !== '' && {
              background: '#5C6BC0',
              color: '#fff',
            },
          ]"
          class="button"
        >
          {{ buttonRequire }}
        </button>
      </div>
    </div>
    <div
      v-if="checkConditional && !checkConditionalFunction()"
      style="margin: -6px 0px 10px; font-size: 10px; color: #d2416d"
    >
      <span class="omrs-input-helper">{{ errorText && errorText }}</span>
    </div>
  </div>
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
    fatherClass: String,
    className: String,
    type: String,
    placeHolder: String,
    name: String,
    vModel: String,
    Style: String,
    errorText: String,
    buttonRequire: String,
    oldPass: String,
    checkConditional: Boolean,
  },
  components: {},
  methods: {
    handleChange: function (e) {
      this.$emit("handleChange", e);
    },
    checkConditionalFunction: function () {
      if (this.name === "password") {
        if (this.vModel.split("").length >= 8) {
          return true;
        }
      } else if (this.name === "confirmPassword") {
        if (this.vModel === this.oldPass) {
          return true;
        }
      } else {
        if (this.vModel !== "") {
          return true;
        }
      }
    },
  },
};
</script>
