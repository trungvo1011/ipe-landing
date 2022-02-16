<template>
  <div class="examples" id="IPEDIT">
    <div class="examples__container">
      <div v-for="(item, index) in data" :key="index" class="cardd exmodule">
        <div class="front">
          <div class="front-img">
            <img :src="item.background" alt="" />
          </div>
          <div class="module-text">
            <div class="text">
              <h2>{{ item.img }}</h2>
              <p>{{ item.text_1 }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/compExamples.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script>
import Banner5 from "../assets/images/example1.svg";
import Banner4 from "../assets/images/example2.svg";
import Banner2 from "../assets/images/example3.svg";
import Banner1 from "../assets/images/example4.svg";
import Banner6 from "../assets/images/example5.svg";
import Banner3 from "../assets/images/example6.svg";
export default {
  data() {
    return {
      data: [
        {
          background: Banner1,
          img: "기능 소개",
          text_1:
            "싸인 찾아다녀도, 하는 방지하는 길지 그들의 몸이 것이다. 웅대한 우리 주는 청춘이 있을 원질.",
        },
        {
          background: Banner2,
          img: "기능 소개",
          text_1:
            "싸인 찾아다녀도, 하는 방지하는 길지 그들의 몸이 것이다. 웅대한 우리 주는 청춘이 있을 원질.",
        },
        {
          background: Banner3,
          img: "기능 소개",
          text_1:
            "싸인 찾아다녀도, 하는 방지하는 길지 그들의 몸이 것이다. 웅대한 우리 주는 청춘이 있을 원질.",
        },
        {
          background: Banner4,
          img: "기능 소개",
          text_1:
            "싸인 찾아다녀도, 하는 방지하는 길지 그들의 몸이 것이다. 웅대한 우리 주는 청춘이 있을 원질.",
        },
        {
          background: Banner5,
          img: "기능 소개",
          text_1:
            "싸인 찾아다녀도, 하는 방지하는 길지 그들의 몸이 것이다. 웅대한 우리 주는 청춘이 있을 원질.",
        },
        {
          background: Banner6,
          img: "기능 소개",
          text_1:
            "싸인 찾아다녀도, 하는 방지하는 길지 그들의 몸이 것이다. 웅대한 우리 주는 청춘이 있을 원질.",
        },
      ],
    };
  },
  components: {},
};
</script>