<template>
  <div class="news" id="New">
    <div class="news__container container">
      <!-- Modal Detail New  -->
      <DetailNew v-bind:isNew="isNew" v-on:closeContact="closeContact" />
      <!-- 1 -->
      <Title title="News" descrip="아이피에딧의 새소식을 알려드립니다" />
      <div class="news-data">
        <div
          v-for="(item, index) in data.slice(dataPlus)"
          :key="index"
          class="content-news"
          v-on:click="openDetail"
        >
          <div class="content-news-img">
            <img :src="item.img" :alt="item.img" />
          </div>
          <div class="content-news-text">
            <p>{{ item.time }}</p>
            <h2>
              {{ item.content }}
            </h2>
          </div>
        </div>
      </div>
      <div class="showMore" @click="showMore">
        <p>더 보기 <img :src="Arrow" :alt="Arrow" /></p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/news.scss";
</style>

<script  type="text/babel">
import PlaceholderImg from "../assets/images/placeholder_img.svg";
import New1 from "../assets/images/news1.svg";
import New2 from "../assets/images/news2.svg";
import New3 from "../assets/images/news3.svg";
import New4 from "../assets/images/news4.svg";
import Arrow from "../assets/images/arrow-expand.svg";
import DetailNew from "./DetailNew.vue";
export default {
  data() {
    return {
      //Imgaes
      PlaceholderImg: PlaceholderImg,
      New1: New1,
      New2: New2,
      New3: New3,
      New4: New4,
      Arrow: Arrow,
      // Variables
      isNew: false,
      activeMenu: false,
      data: [
        {
          img: PlaceholderImg,
          time: "2021.10.10",
          content:
            "보는 두손을 가는 용감하고 내려온 봄바람을 우는 것이다. 보라, 얼마나 있는가 것이다.",
        },
        {
          img: New1,
          time: "2021.10.10",
          content:
            "지나가는 책상을 너무나 봅니다. 소학교 풀이 다하지 나는 당신은 못 청춘이 아무 이름들을 까닭입니다...",
        },
        {
          img: New2,
          time: "2021.10.10",
          content:
            "인간의 현저하게 그들의 가장 보라. 쓸쓸한 희망의 것이다.보라, 하는 발휘하기 수 사막이다.",
        },
        {
          img: New3,
          time: "2021.10.10",
          content:
            "못할 황금시대를 인간에 심장의 있는 우리의 얼마나 타오르고 봄바람이다. 옷을 사람은 스며들어..",
        },
        {
          img: New4,
          time: "2021.10.10",
          content:
            "못할 황금시대를 인간에 심장의 있는 우리의 얼마나 타오르고 봄바람이다. 옷을 사람은 스며들어..",
        },
        {
          img: PlaceholderImg,
          time: "2021.10.10",
          content:
            "보는 두손을 가는 용감하고 내려온 봄바람을 우는 것이다. 보라, 얼마나 있는가 것이다.",
        },
        {
          img: New3,
          time: "2021.10.10",
          content:
            "못할 황금시대를 인간에 심장의 있는 우리의 얼마나 타오르고 봄바람이다. 옷을 사람은 스며들어..",
        },
        {
          img: New1,
          time: "2021.10.10",
          content:
            "지나가는 책상을 너무나 봅니다. 소학교 풀이 다하지 나는 당신은 못 청춘이 아무 이름들을 까닭입니다...",
        },
        {
          img: New2,
          time: "2021.10.10",
          content:
            "인간의 현저하게 그들의 가장 보라. 쓸쓸한 희망의 것이다.보라, 하는 발휘하기 수 사막이다.",
        },
        {
          img: New3,
          time: "2021.10.10",
          content:
            "못할 황금시대를 인간에 심장의 있는 우리의 얼마나 타오르고 봄바람이다. 옷을 사람은 스며들어..",
        },
        {
          img: New4,
          time: "2021.10.10",
          content:
            "못할 황금시대를 인간에 심장의 있는 우리의 얼마나 타오르고 봄바람이다. 옷을 사람은 스며들어..",
        },
      ],
      dataPlus: 5,
    };
  },
  methods: {
    // Contact
    closeContact: function () {
      document.querySelector("html").classList.remove("is-clipped");
      this.isNew = false;
    },
    openDetail: function () {
      document.querySelector("html").classList.add("is-clipped");
      this.isNew = true;
      this.activeMenu = false;
    },
    showMore: function () {
      if (this.dataPlus > 0) {
        this.dataPlus = this.dataPlus - 1;
      } else {
        this.dataPlus = this.dataPlus;
      }
    },
  },
  created() {
    this.dataPlus = this.data.length - 5;
  },
  components: { DetailNew },
};
</script>
