<template>
  <div>
    <Header />
    <Banner />
    <!-- <Impactory /> -->
    <Competitor />
    <Features />
    <!-- <CompExamples /> -->
    <News />
    <Certifications />
    <Pricing />
    <UseFree />
    <Footer />
    <Reset />
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/global.scss";
@import "../assets/stylesheets/main.sass";
</style>;

<script>
import Header from "../container/Header.vue";
import Footer from "../container/Footer.vue";
import Banner from "../container/Banner.vue";
import Impactory from "../container/Impactory.vue";
import Competitor from "../container/Competitor.vue";
import CompExamples from "../container/CompExamples.vue";
import UseFree from "../container/UseFree.vue";
import Reset from "../container/ResetPassword.vue";
import Features from "~~/container/Features.vue";
import News from "~~/container/News.vue";
import Certifications from "~~/container/Certifications.vue";
import Pricing from "~~/container/Pricing.vue";

export default {
  data() {
    return {};
  },
  methods: {},
  created() {
    if (process.client) {
      document.querySelector("html").style.scrollBehavior = "smooth";
    }
  },

  components: {
    Reset,
    Header,
    Banner,
    Competitor,
    UseFree,
    Impactory,
    CompExamples,
    Footer,
    Features,
    News,
    Certifications,
    Pricing,
  },
};
</script>
