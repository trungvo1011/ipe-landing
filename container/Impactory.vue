<template>
  <div class="impactory" id="Impact" v-on:scroll="scrollFunction">
    <div class="impactory__container containerr">
      <div
        class="video"
        v-bind:style="[
          !modalVideo && { backgroundImage: 'url(' + videoArea + ')' },
        ]"
      >
        <div class="vide-background" v-if="!modalVideo">
          <img :src="videoArea" />
        </div>
        <iframe
          v-if="modalVideo"
          class="iframe-desktop"
          width="100%"
          height="100%"
          src="https://www.youtube.com/embed/hF5b-9iAN1k?autoplay=1"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>

        <div
          class="video-img video-img-desktop"
          :style="[modalVideo ? { display: 'none' } : { display: 'flex' }]"
          v-on:click="handlePlay"
        >
          <img :src="playCircle" />
        </div>
        <!-- <div class="vide-background" v-if="width < 991 && modalVideo">
          <img :src="videoArea" />
        </div> -->
        <!-- <div
          v-if="width < 991"
          class="video-img video-img-desktop"
          v-on:click="handlePlay(width >= 991 ? 'normal' : 'modal')"
        >
          <img :src="playCircle" />
        </div> -->
      </div>

      <!-- modal video -->

      <!-- <div
        class="modal"
        v-bind:class="{ 'is-active': modalVideo }"
        v-if="width < 991 && modalVideo"
      >
        <div class="modal-content">
          <button
            class="modal-close is-large"
            aria-label="close"
            v-on:click="handlePlay('modal')"
          ></button>
          <iframe
            src="https://www.youtube.com/embed/hF5b-9iAN1k"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
      </div> -->

      <div class="box-containe" id="minutes__top__con">
        <div
          class="module top-module_1"
          style="padding: 38px 60px"
          v-on:scroll="scrollFunction"
        >
          <div class="top">
            <!-- left -->
            <div class="left">
              <div class="left__top">
                <p>1페이지 기준</p>
                <h3>5분</h3>
              </div>
              <div class="left__bottom">MS Word</div>
            </div>
            <!-- rignht -->
            <div class="right">
              <div class="percent">
                <h1>60%</h1>
                <h2>빠르게!</h2>
              </div>
              <div class="minutes" v-on:click="animationModule">
                <div class="minutes__top" id="minutes__top">
                  <p>1페이지 기준</p>
                  <h2>2분</h2>
                </div>
                <div class="minutes__bottom">IPEDIT</div>
              </div>
            </div>
          </div>
          <div
            class="bottom"
            v-bind:style="{ backgroundImage: 'url(' + highlight + ')' }"
            style="width: 114px"
          >
            <p>작업 시간</p>
          </div>
        </div>

        <div class="module" style="padding: 38px 30px">
          <div class="top top-module_2">
            <h1>NO</h1>
            <!-- <h2>청구항 인용 오류</h2> -->
          </div>
          <div
            class="bottom"
            v-bind:style="{ backgroundImage: 'url(' + highlight + ')' }"
            style="width: 87px"
          >
            <p>품질</p>
          </div>

          <div class="contentt">
            <div class="contentt__container wrapper">
              <ul class="contentt__container__listt words">
                <li class="contentt__container__listt__itemm span">
                  구성요소 오류
                </li>
                <li class="contentt__container__listt__itemm span">
                  선행사 오류
                </li>
                <li class="contentt__container__listt__itemm span">
                  청구항 인용 오류
                </li>
                <li class="contentt__container__listt__itemm span">
                  선행사 오류
                </li>
                <li class="contentt__container__listt__itemm span">
                  구성요소 오류
                </li>
              </ul>
            </div>
          </div>
        </div>

        <div class="module" style="padding: 38px 30px">
          <div class="top top-module_3">
            <div class="top-img">
              <img :src="korea" />
            </div>
            <div class="top-img">
              <img :src="usa" />
            </div>
            <div class="top-img">
              <img :src="sec" />
            </div>
            <div class="top-img">
              <img :src="japan" />
            </div>
          </div>
          <div
            class="bottom"
            v-bind:style="{ backgroundImage: 'url(' + highlight + ')' }"
            style="width: 127px"
          >
            <p>사용 국가</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/impactory.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script>
import VideoArea from "../assets/images/VideoArea.svg";
import Rectangle3 from "../assets/images/Rectangle 3.svg";
import Rectangle6 from "../assets/images/Rectangle 6.svg";
import Highlight from "../assets/images/img_highlight_1.svg";
import Korea from "../assets/images/Korea.svg";
import USA from "../assets/images/USA.svg";
import Sec from "../assets/images/Sec.svg";
import Japan from "../assets/images/Japan.svg";
import Playcircle from "../assets/images/playcircle.svg";
export default {
  data() {
    return {
      videoArea: VideoArea,
      rectangle3: Rectangle3,
      rectangle6: Rectangle6,
      highlight: Highlight,
      korea: Korea,
      japan: Japan,
      playCircle: Playcircle,
      sec: Sec,
      usa: USA,
      modalVideo: false,
      videoDesktop: true,
      animate: false,
      width: "",
    };
  },
  components: {},
  methods: {
    handlePlay: function () {
      this.modalVideo = !this.modalVideo;
    },
    handleResize() {
      if (typeof window !== "undefined") {
        this.width = window.innerWidth;
      }
    },

    scrollFunction: function () {
      if (process.client) {
        if (typeof window !== "undefined") {
          if (
            window.scrollY >
            document.getElementById("minutes__top__con").offsetTop + 2000
          ) {
            document
              .getElementById("minutes__top")
              .classList.remove("minutes__top__animation");
          }
          if (
            window.scrollY >=
            document.getElementById("minutes__top__con").offsetTop
          ) {
            document
              .getElementById("minutes__top")
              .classList.add("minutes__top__animation");
          } else {
            document
              .getElementById("minutes__top")
              .classList.remove("minutes__top__animation");
          }
        }
      }
    },
    animationModule: function () {
      this.animate = true;
      document
        .getElementById("minutes__top")
        .classList.add("minutes__top__animation");
    },
  },
  created() {
    if (this.width < 1000 && this.width > 1400) {
      this.animate = false;
    }
    if (typeof window !== "undefined") {
      window.addEventListener("scroll", this.scrollFunction);
      window.addEventListener("resize", this.handleResize);
      this.handleResize();
      window.addEventListener("keydown", (evt) => {
        evt = evt || window.event;
        if (evt.keyCode == 27) {
          this.modalVideo = false;
        }
      });
    }
  },
};
</script>
