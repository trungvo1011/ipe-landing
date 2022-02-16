<template>
  <div class="competitor" id="Work">
    <div class="competitor__container containerr">
      <Title title="How it works" descrip="IPEDIT을 이용한 명세서 작성" />
      <!-- Round  -->
      <div class="assistant">
        <!-- 1 -->
        <div class="round" v-on:click="handleRound(1)">
          <div
            class="round-img"
            v-bind:class="{ isActive: roundIndex === 1 }"
            :style="[
              roundIndex > 1 && {
                background: '#7c7f91 !important',
                opacity: '1 !important',
              },
            ]"
          >
            <img :src="Add" :alt="Add" />
          </div>
          <!-- <div
            class="round-text"
            :style="[
              roundIndex === 1
                ? { color: '#5c6bc0', opacity: '1 !important' }
                : roundIndex > 1
                ? { color: '#7c7f91', opacity: '1 !important' }
                : {},
            ]"
          >
            <p>구성요소<br />등록</p>
          </div> -->
        </div>
        <div class="arrow">
          <img :src="Arrow" :alt="Arrow" v-if="roundIndex === 1" />
          <img :src="ArrowActive" :alt="ArrowActive" v-if="roundIndex === 2" />
          <img :src="ArrowDone" :alt="ArrowDone" v-if="roundIndex === 3" />
        </div>
        <!-- 2 -->
        <div class="round" v-on:click="handleRound(2)">
          <div
            class="round-img"
            v-bind:class="{ isActive: roundIndex === 2 }"
            :style="[
              roundIndex > 2 && {
                background: '#7c7f91 !important',
                opacity: '1 !important',
              },
            ]"
          >
            <img :src="Edit" :alt="Edit" />
          </div>
          <!-- <div
            class="round-text"
            :style="[
              roundIndex === 2
                ? { color: '#5c6bc0', opacity: '1 !important' }
                : roundIndex > 2
                ? { color: '#7c7f91', opacity: '1 !important' }
                : {},
            ]"
          >
            <p>
              구성요소 자동완성과<br />등록AI Assistant를 이용한 명세서 작성
            </p>
          </div> -->
        </div>
        <div class="arrow">
          <img :src="Arrow" :alt="Arrow" v-if="roundIndex !== 3" />
          <img :src="ArrowActive" :alt="ArrowActive" v-if="roundIndex > 2" />
        </div>
        <!-- 3 -->
        <div class="round" v-on:click="handleRound(3)">
          <div class="round-img" v-bind:class="{ isActive: roundIndex === 3 }">
            <img :src="Download" :alt="Download" />
          </div>
          <!-- <div
            class="round-text"
            :style="[
              roundIndex === 3 && { color: '#5c6bc0', opacity: '1 !important' },
            ]"
          >
            <p>완성된 결과물 <br />다운로드</p>
          </div> -->
        </div>
      </div>
      <!-- Text  -->
      <div class="assistant assistant-text">
        <!-- 1 -->
        <div class="round" v-on:click="handleRound(1)">
          <div
            class="round-text"
            :style="[
              roundIndex === 1
                ? { color: '#5c6bc0', opacity: '1 !important' }
                : roundIndex > 1
                ? { color: '#7c7f91', opacity: '1 !important' }
                : {},
            ]"
          >
            <p>구성요소<br />등록</p>
          </div>
        </div>
        <!-- 2 -->
        <div class="round" v-on:click="handleRound(2)">
          <div
            class="round-text"
            :style="[
              roundIndex === 2
                ? { color: '#5c6bc0', opacity: '1 !important' }
                : roundIndex > 2
                ? { color: '#7c7f91', opacity: '1 !important' }
                : {},
            ]"
          >
            <p>
              구성요소 자동완성과<br />등록AI Assistant를 이용한 명세서 작성
            </p>
          </div>
        </div>

        <!-- 3 -->
        <div class="round" v-on:click="handleRound(3)">
          <div
            class="round-text"
            :style="[
              roundIndex === 3 && { color: '#5c6bc0', opacity: '1 !important' },
            ]"
          >
            <p>완성된 결과물 <br />다운로드</p>
          </div>
        </div>
      </div>
      <!-- Screen Round  -->
      <!-- Screen Round 1  -->
      <div
        class="screen-containe"
        v-for="(item, index) in screenList"
        :key="index"
      >
        <div
          v-if="item.id === roundIndex"
          class="screen"
          :class="`${
            roundIndex === 2
              ? 'screenActive2'
              : roundIndex === 3
              ? 'screenActive3'
              : ''
          }`"
        >
          <div class="screen__img">
            <img :src="item.img" :alt="item.img" />
          </div>
          <div class="screen__text">
            <h2>{{ item.title }}</h2>
            <ul>
              <li><img :src="Tick" :alt="Tick" />자유로운 구성요소 활용</li>
              <li><img :src="Tick" :alt="Tick" />도면 자동 등록</li>
              <li><img :src="Tick" :alt="Tick" />엑셀 리스트 등록</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/competitor.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script  type="text/babel">
import Add from "../assets/images/add-one.svg";
import Edit from "../assets/images/edit-one.svg";
import Download from "../assets/images/download.svg";
import Arrow from "../assets/images/arrow.svg";
import ArrowActive from "../assets/images/arrow-active.svg";
import ArrowDone from "../assets/images/arrow-done.svg";
import ScreenAssistant from "../assets/images/screen_assistant.svg";
import Tick from "../assets/images/tick__icon.svg";
import ICountUp from "vue-countup-v2";
export default {
  data() {
    return {
      //Imgaes
      Add: Add,
      Edit: Edit,
      Download: Download,
      Arrow: Arrow,
      ArrowActive: ArrowActive,
      ArrowDone: ArrowDone,
      ScreenAssistant: ScreenAssistant,
      Tick: Tick,
      // Variables
      roundIndex: 1,
      screenList: [
        {
          id: 1,
          img: ScreenAssistant,
          title: "구성요소 등록",
          description: [
            "자유로운 구성요소 활용",
            "도면 자동 등록",
            "엑셀 리스트 등록",
          ],
        },
        {
          id: 2,
          img: ScreenAssistant,
          title: "구성요소 자동완성과 AI Assistant를 이용한 명세서 작성",
          description: [
            "템플릿 활용",
            "관용표현 활용",
            "청구항 마법사",
            "완벽한 데이터 보안",
          ],
        },
        {
          id: 3,
          img: ScreenAssistant,
          title: "완성된 결과물 다운로드",
          description: [
            "일부 내용 자동 생성",
            "명세서 양식에 맞춘 파일 생성",
            "완벽한 데이터 보안",
          ],
        },
      ],
    };
  },
  methods: {
    handleRound: function (index) {
      this.roundIndex = index;
    },
  },

  components: { ICountUp },
};
</script>
