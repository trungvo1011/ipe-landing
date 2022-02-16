<template>
  <div class="hompage-baner" v-on:scroll="scrollFunction">
    <div
      class="radio-btns__btn"
      v-for="(item, index) in arrData"
      :key="index"
      v-bind:style="{ backgroundImage: 'url(' + item.background + ')' }"
      :class="item.class"
    >
      <div class="containe">
        <div class="containe__text">
          <p
            class="typewrite"
            data-period="2000"
            data-type='[ "아직도 워드나 통합명세서 작성기로 명세서 쓰세요?", "명세서 작성을 위한 야근은 이제 그만!", "저녁이 있는 삶, IPEDIT가 만들어 드리겠습니다", "작성자도 리뷰어도 모두 만족시켜 드리겠습니다", "IPEDIT로 다른 대리인과  비교 평가에서 우위에 서세요!" ]'
          >
            <span class="wrap"></span>
          </p>
        </div>
      </div>
    </div>
    <div class="arrowExpand" v-on:click="scrollToHeader('Work')">
      <img :src="ArrowExpand" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/banner.scss";
</style>

<script>
import Banner1 from "../assets/images/baner_draft2.svg";
import Banner2 from "../assets/images/baner2.svg";
import Draft from "../assets/images/draft.svg";
import ArrowExpand from "../assets/images/arrow-expand-white.svg";
export default {
  data() {
    return {
      banner1: Banner1,
      banner2: Banner2,
      ArrowExpand: ArrowExpand,
      arrData: [
        {
          background: Banner1,
          img: Draft,
          title: "아직도 워드나 통합명세서 작성기로명세서 쓰세요?",
          description: "",
          btn: "특허 명세서 작성하러 가기",
          color: "color: #5c6bc0 !important",
          class: "hompage-baner__left",
        },
      ],
    };
  },
  methods: {
    scrollToHeader: function (type) {
      let offset = document.getElementById(type)?.offsetTop;
      if (typeof window !== "undefined") {
        switch (type) {
          case "Work":
            window.scrollTo(0, offset);
            break;

          default:
            break;
        }
      }
    },
    scrollFunction: function () {
      console.log("a");
      if (process.client) {
        if (typeof window !== "undefined") {
          console.log(window.screenY);
        }
      }
    },
  },

  created() {
    var TxtType = function (el, toRotate, period) {
      this.toRotate = toRotate;
      this.el = el;
      this.loopNum = 0;
      this.period = parseInt(period, 10) || 2000;
      this.txt = "";
      this.tick();
      this.isDeleting = false;
    };

    TxtType.prototype.tick = function () {
      var i = this.loopNum % this.toRotate.length;
      var fullTxt = this.toRotate[i];

      if (this.isDeleting) {
        this.txt = fullTxt.substring(0, this.txt.length - 1);
      } else {
        this.txt = fullTxt.substring(0, this.txt.length + 1);
      }

      this.el.innerHTML = '<span class="wrap">' + this.txt + "</span>";

      var that = this;
      var delta = 200 - Math.random() * 300;

      if (this.isDeleting) {
        delta /= 2;
      }

      if (!this.isDeleting && this.txt === fullTxt) {
        delta = this.period;
        this.isDeleting = true;
      } else if (this.isDeleting && this.txt === "") {
        this.isDeleting = false;
        this.loopNum++;
        delta = 500;
      }

      setTimeout(function () {
        that.tick();
      }, delta);
    };
    if (process.client) {
      window.onload = function () {
        var elements = document.getElementsByClassName("typewrite");
        for (var i = 0; i < elements.length; i++) {
          var toRotate = elements[i].getAttribute("data-type");
          var period = elements[i].getAttribute("data-period");
          if (toRotate) {
            new TxtType(elements[i], JSON.parse(toRotate), period);
          }
        }
        // INJECT CSS
        var css = document.createElement("style");
        css.type = "text/css";
        css.innerHTML = ".typewrite > .wrap { border-right: 0.08em solid #fff}";
        document.body.appendChild(css);
      };
    }
  },
};
</script>
