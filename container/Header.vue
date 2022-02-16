<template>
  <nav
    class="navbar"
    role="navigation"
    aria-label="main navigation"
    v-on:scroll="scrollFunction"
    :style="[
      heightScreen < 700 && { background: 'transparent', height: '120px' },
    ]"
  >
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
    <ContactUs v-bind:isContact="isContact" v-on:closeContact="closeContact" />

    <div class="navbar-brand">
      <a class="navbar-item logo" href="/">
        <img
          :src="Draft"
          alt="draft"
          width="112"
          height="28"
          :style="[
            heightScreen > 700 && {
              filter:
                'invert(0%) sepia(87%) saturate(7459%) hue-rotate(172deg) brightness(0%) contrast(108%)',
            },
          ]"
        />
      </a>

      <!-- responsive-edd -->
      <div class="responsive-edd">
        <div
          class="navbar-end endd"
          v-bind:class="{ 'navbar-start__scroll': heightScreen > 700 }"
        >
          <div class="navbar-item" style="margin-right: 0">
            <div class="buttons">
              <div class="navbar-item has-dropdown is-hoverable">
                <a class="navbar-link" v-on:click="activeEdd = !activeEdd">
                  {{ language }}
                </a>
                <div
                  class="navbar-dropdown"
                  v-bind:class="{ showDropEdd: !activeEdd }"
                  style="z-index: 111111"
                >
                  <a
                    v-for="(item, index) in arrLanguage"
                    :key="index"
                    class="navbar-item"
                    style="margin-right: 0; width: 100%; white-space: nowrap"
                    v-on:click="handleLanguage(item)"
                  >
                    <p>{{ item }}</p>
                  </a>
                </div>
              </div>
              <a class="navbar-item item-log" v-on:click="openModalLogin">
                로그인
              </a>
              <a class="button btn" v-on:click="openModalSignUp">
                무료회원가입
              </a>
            </div>
          </div>
        </div>
        <a
          role="button"
          class="navbar-burger isActive"
          v-bind:class="{ 'is-active': activeMenu }"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbarBasicExample"
          v-on:click="activeMenu = !activeMenu"
        >
          <span
            aria-hidden="true"
            :style="[heightScreen > 700 && { background: '#61657E' }]"
          ></span>
          <span
            aria-hidden="true"
            :style="[heightScreen > 700 && { background: '#61657E' }]"
          ></span>
          <span
            aria-hidden="true"
            :style="[heightScreen > 700 && { background: '#61657E' }]"
          ></span>
        </a>
      </div>
    </div>

    <div
      id="navbarBasicExample"
      class="navbar-menu"
      v-bind:class="{ 'is-active': activeMenu }"
    >
      <div
        class="navbar-start"
        v-bind:class="{ 'navbar-start__scroll': heightScreen > 700 }"
      >
        <a class="navbar-item" v-on:click="scrollToHeader('Work')">
          How it works
        </a>
        <a class="navbar-item" v-on:click="scrollToHeader('Features')">
          Features
        </a>
        <a class="navbar-item" v-on:click="scrollToHeader('New')"> News </a>
        <a class="navbar-item" v-on:click="scrollToHeader('Certifications')">
          Certifications
        </a>
        <a class="navbar-item" v-on:click="scrollToHeader('Pricing')">
          Pricing
        </a>
        <a class="navbar-item" v-on:click="openContact"> Contact us </a>
        <a
          class="
            navbar-item navbar-item-modal
            item-login-header
            respon-text-signup
          "
          v-on:click="openModalLogin"
        >
          로그인
        </a>
        <a class="button btn btn-respon" v-on:click="openModalSignUp">
          무료회원가입
        </a>
      </div>

      <div
        class="navbar-end"
        v-bind:class="{ 'navbar-start__scroll': heightScreen > 700 }"
      >
        <div
          class="navbar-item"
          style="padding-right: 0; margin-right: 0; padding-top: 8px !important"
        >
          <div class="buttons">
            <div
              class="navbar-item"
              v-bind:class="{ 'has-dropdown is-hoverable': !upHere }"
            >
              <a
                class="navbar-link"
                v-bind:class="getClass()"
                style="width: max-content; background: none; height: 50px"
                v-on:mouseleave="upHere = false"
              >
                {{ language }}
              </a>
              <div class="navbar-dropdown" style="margin-top: -4px">
                <a
                  v-for="(item, index) in arrLanguage"
                  :key="index"
                  class="navbar-item"
                  style="margin-right: 0; width: 100%; white-space: nowrap"
                  v-on:click="handleLanguage(item)"
                  v-on:mouseleave="upHere = false"
                >
                  <p>{{ item }}</p>
                </a>
              </div>
            </div>
            <a
              class="navbar-item navbar-item-modal item-login-header"
              v-on:click="openModalLogin"
              v-bind:class="{ work: heightScreen > 700 }"
            >
              로그아웃
            </a>
            <Button v-on:click="openModalSignUp" text="무료회원가입"> </Button>
          </div>
        </div>
        <a
          role="button"
          class="navbar-burger isActive"
          v-bind:class="{ 'is-active': activeMenu }"
          aria-label="menu"
          aria-expanded="true"
          data-target="navbarBasicExample"
          v-on:click="activeMenu = !activeMenu"
        >
          <span
            aria-hidden="true"
            :style="[heightScreen > 700 && { background: '#61657E' }]"
          ></span>
          <span
            aria-hidden="true"
            :style="[heightScreen > 700 && { background: '#61657E' }]"
          ></span>
          <span
            aria-hidden="true"
            :style="[heightScreen > 700 && { background: '#61657E' }]"
          ></span>
        </a>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/header.scss";
@import "../assets/stylesheets/main.sass";
</style>

<script>
import Login from "./Login.vue";
import SignUp from "./SignUp.vue";
import ContactUs from "./ContactUs.vue";
import Draft from "../assets/images/draft.svg";
export default {
  data() {
    return {
      Draft: Draft,
      activeMenu: false,
      activeEdd: false,
      activeDropdown: false,
      modalLogin: false,
      modalSignup: false,
      isContact: false,
      upHere: false,
      language: "한국어",
      arrLanguage: ["English", "日本語"],
      heightScreen: 0,
    };
  },
  components: { Login, SignUp, ContactUs },
  methods: {
    // scroll
    scrollFunction: function () {
      if (process.client) {
        if (typeof window !== "undefined") {
          this.heightScreen = window.scrollY;
        }
      }
    },
    //class
    getClass: function () {
      return {
        "dropdown-option": !this.upHere,
        work: this.heightScreen > 700,
      };
    },
    // login
    openModalLogin: function () {
      document.querySelector("html").classList.add("is-clipped");
      localStorage.setItem("openModal", true);
      this.modalLogin = true;
      this.activeMenu = false;
    },
    changeModalLogin: function () {
      document.querySelector("html").classList.remove("is-clipped");
      localStorage.setItem("openModal", false);
      this.modalLogin = false;
    },
    // Register
    openModalSignUp: function () {
      document.querySelector("html").classList.add("is-clipped");
      this.modalSignup = true;
      this.activeMenu = false;
    },
    changeModalSignUp: function () {
      document.querySelector("html").classList.remove("is-clipped");
      this.modalSignup = false;
    },
    // Contact
    openContact: function () {
      document.querySelector("html").classList.add("is-clipped");
      this.isContact = true;
      this.activeMenu = false;
    },
    closeContact: function () {
      document.querySelector("html").classList.remove("is-clipped");
      this.isContact = false;
    },
    handleLanguage: function (lang) {
      this.language = lang;
      this.upHere = true;
      this.activeEdd = false;
      if (lang === "English") {
        this.arrLanguage = ["한국어", "日本語"];
      } else if (lang === "한국어") {
        this.arrLanguage = ["English", "日本語"];
      } else {
        this.arrLanguage = ["한국어", "English"];
      }
    },
    scrollToHeader: function (type) {
      this.activeMenu = false;
      if (process.client) {
        let offset = document.getElementById(type)?.offsetTop;
        if (typeof window !== "undefined") {
          switch (type) {
            case "Work":
              window.scrollTo(0, offset);
              break;
            case "Features":
              window.scrollTo(0, offset);
              break;
            case "New":
              window.scrollTo(0, offset);
              break;
            case "Certifications":
              window.scrollTo(0, offset);
              break;
            case "Pricing":
              window.scrollTo(0, offset);
              break;
            default:
              break;
          }
        }
      }
    },
  },
  created() {
    if (typeof window !== "undefined") {
      window.addEventListener("scroll", this.scrollFunction);
    }
  },
};
</script>
