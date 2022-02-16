<template>
  <div class="pricing" id="Pricing">
    <div class="pricing__container containerr">
      <Title title="Pricing" descrip="특허명세서 작성을 위한 올인원 솔루션" />
      <!-- tab  -->
      <div class="container-tab">
        <!-- style arrow %  -->

        <!-- tabb content  -->
        <div class="tab-a-arrow">
          <div class="arrow-up">
            <p>Save 10%</p>
            <img :src="ArrowUp" :alt="ArrowUp" />
          </div>
          <div class="tab-percent">
            <div class="tabss">
              <input type="radio" id="radio-1" name="tabs" />
              <label
                class="tabb"
                for="radio-1"
                v-on:click="ShowTabContent(1)"
                v-bind:class="{ isActive: idTabs === 1 }"
              >
                1개월
              </label>
              <input type="radio" id="radio-2" name="tabs" />
              <label
                class="tabb"
                for="radio-2"
                v-on:click="ShowTabContent(2)"
                v-bind:class="{ isActive: idTabs === 2 }"
              >
                6개월
              </label>
              <input type="radio" id="radio-3" name="tabs" />
              <label
                class="tabb"
                for="radio-3"
                v-on:click="ShowTabContent(3)"
                v-bind:class="{ isActive: idTabs === 3 }"
              >
                1년
              </label>
              <span class="glider"></span>
            </div>
            <div class="arrow-turn">
              <p>Save 30%</p>
              <img class="arrow-up-desktop" :src="ArrowTurn" :alt="ArrowTurn" />
              <img class="arrow-up-mobile" :src="ArrowUp" :alt="ArrowUp" />
            </div>
          </div>
        </div>

        <!-- select  -->
        <div class="navbar-item has-dropdown is-hoverable tabss kipo">
          <a class="navbar-link" v-on:click="activeEdd = !activeEdd">
            <p style="display: flex; align-items: center">
              특허명세서 양식 <span>{{ language }}</span>
            </p>
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
      </div>
      <!-- box  -->
      <div class="cardd exmodule">
        <div class="front" v-for="(item, index) in data" :key="index">
          <div class="module-text">
            <div class="text">
              <h3>{{ item.title }}</h3>
              <h2>${{ item.price }} <span>/ 월</span></h2>
              <p>{{ item.descrip }}</p>
              <ul>
                <li v-for="(o, indexO) in item.benefits" :key="indexO">
                  <img :src="Tick" :alt="Tick" />{{ o }}
                </li>
              </ul>
            </div>
            <div class="button-buy">
              <button>무료체험하기</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/pricing.scss";
// @import "../assets/stylesheets/header.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script>
import Tick from "../assets/images/tick__icon.svg";
import ArrowExpand from "../assets/images/arrow-expand.svg";
import ArrowUp from "../assets/images/arrow-up.svg";
import ArrowTurn from "../assets/images/arrow-turn.svg";
export default {
  data() {
    return {
      Tick: Tick,
      ArrowExpand: ArrowExpand,
      ArrowUp: ArrowUp,
      ArrowTurn: ArrowTurn,
      idTabs: 1,
      activeEdd: false,
      language: "KIPO",
      arrLanguage: ["KIPO", "USPTO", "JPO"],
      data: [
        {
          title: "Basic",
          price: "49",
          descrip: "소규모 팀에서 다양한 기능을 활용할 수 있습니다",
          benefits: [
            "한 달에 5건",
            "한 달에 500,000개 단어",
            "암호화 데이터 저장",
          ],
        },
        {
          title: "Standard",
          price: "99",
          descrip: "비즈니스를 확장하고 생산성을 향상시키기에 적합합니다",
          benefits: [
            "한 달에 5건",
            "한 달에 500,000개 단어",
            "암호화 데이터 저장",
            "클라우드 저장",
          ],
        },
        {
          title: "Premium",
          price: "299",
          descrip:
            "규제 사항을 준수하기 위한 유연성과 성장에 걸맞은 기능을 제공합니다",
          benefits: [
            "한 달에 5건",
            "한 달에 500,000개 단어",
            "암호화 데이터 저장",
            "클라우드 저장",
            "서식적용 번역 리포트",
          ],
        },
      ],
    };
  },
  methods: {
    ShowTabContent: function (data) {
      this.idTabs = data;
    },
    handleLanguage: function (lang) {
      this.language = lang;
      this.upHere = true;
      this.activeEdd = false;
    },
  },
  components: {},
};
</script>