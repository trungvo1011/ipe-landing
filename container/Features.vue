<template>
  <div class="features" id="Features">
    <div class="features__container containerr">
      <!-- 1 -->
      <Title title="Features" descrip="구성요소 자동완성 에디터 체험하기" />
      <div class="introductions">
        <div class="img-intros">
          <img :src="ScreenFeature2" :alt="ScreenFeature2" />
        </div>
        <div class="text-intros">
          <h2>이렇게 써보세요!</h2>
          <p>
            방지하는 수 풍부하게 충분히 트고, 것이다. 그것을 너의 이것은 지혜는
            인간의 약동하다. 있는 자신과 트고, 붙잡아 이것이야말로 피고,
            위하여서. 아니한 관현악이며, 위하여, 사라지지 청춘은 공자는 열락의
            새 것이다. 길지 그들은 별과 끓는다.<br />
            <br />
            충분히 새가 사람은 소리다.이것은 없는 용감하고 청춘을 때문이다.
            때에, 사는가 예수는 것은 열매를 피어나는 작고 사막이다. 봄바람을
            없는 힘차게 일월과 있다. 위하여, 보배를 관현악이며, 가장 커다란
            노래하며 부패뿐이다.<br />
            <br />
            실로 주는 피고 인도하겠다는 수 보라.
          </p>
        </div>
      </div>
      <!-- 2 -->
      <Title class="feture-respon" descrip="청구항 마법사 체험하기" />
      <div class="introductions introductions__2">
        <div class="text-intros">
          <div class="container">
            <div class="accordion">
              <div
                class="accordion-item"
                v-for="(item, index) in data"
                :key="index"
              >
                <button
                  :id="`accordion-button-${index}`"
                  aria-expanded="false"
                  v-on:click="toggleAccordion(index)"
                >
                  <span class="accordion-title">{{ item.title }}</span>
                  <img :src="Expanded" alt="" />
                </button>
                <div class="accordion-content">
                  <p>
                    {{ item.content }}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="img-intros">
          <img :src="ScreenFeature1" :alt="ScreenFeature1" />
        </div>
      </div>
      <!-- 3 -->
      <Title
        title=""
        descrip="그외에도 다양한 기능이 있어요"
        class="feture-respon"
      />
      <CompExamples />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/features.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script  type="text/babel">
import CompExamples from "./CompExamples.vue";
import ScreenFeature1 from "../assets/images/example4.svg";
import ScreenFeature2 from "../assets/images/example4.svg";
import Expanded from "../assets/images/arrow-expand.svg";
export default {
  data() {
    return {
      //Imgaes
      ScreenFeature1: ScreenFeature1,
      ScreenFeature2: ScreenFeature2,
      Expanded: Expanded,
      // Variables
      data: [
        {
          title: "청구항 삽입하기",
          content:
            "얼마나 반짝이는 그들은 미인을 천지는 같이, 듣는다. 내려온 그들의 모래뿐일 품에 사는가 우리의 들어 있는가? 별과 황금시대를 길지 옷을 싶이 실로 아니다. 싶이 소리다.이것은 생생하며, 가는 희망의 소담스러운 생의 그들의 평화스러운 말이다. 피에 능히 얼음이 피가 것은 예가 용감하고 꽃이 같이, 그리하였는가? 따뜻한 그들의 보이는 이 이것이다. 물방아 긴지라 크고 청춘의 것이다. 것이다.보라, 품에 석가는 아니다. 능히 있는 이것이야말로 기쁘며, 얼음 가지에 영원히 피다.",
        },
        {
          title: "청구항 삭제하기",
          content:
            "얼마나 반짝이는 그들은 미인을 천지는 같이, 듣는다. 내려온 그들의 모래뿐일 품에 사는가 우리의 들어 있는가? 별과 황금시대를 길지 옷을 싶이 실로 아니다. 싶이 소리다.이것은 생생하며, 가는 희망의 소담스러운 생의 그들의 평화스러운 말이다. 피에 능히 얼음이 피가 것은 예가 용감하고 꽃이 같이, 그리하였는가? 따뜻한 그들의 보이는 이 이것이다. 물방아 긴지라 크고 청춘의 것이다. 것이다.보라, 품에 석가는 아니다. 능히 있는 이것이야말로 기쁘며, 얼음 가지에 영원히 피다.",
        },
        {
          title: "청구항 이동하기",
          content:
            "얼마나 반짝이는 그들은 미인을 천지는 같이, 듣는다. 내려온 그들의 모래뿐일 품에 사는가 우리의 들어 있는가? 별과 황금시대를 길지 옷을 싶이 실로 아니다. 싶이 소리다.이것은 생생하며, 가는 희망의 소담스러운 생의 그들의 평화스러운 말이다. 피에 능히 얼음이 피가 것은 예가 용감하고 꽃이 같이, 그리하였는가? 따뜻한 그들의 보이는 이 이것이다. 물방아 긴지라 크고 청춘의 것이다. 것이다.보라, 품에 석가는 아니다. 능히 있는 이것이야말로 기쁘며, 얼음 가지에 영원히 피다.",
        },
      ],
    };
  },
  methods: {
    toggleAccordion: function (index) {
      const items = document.querySelectorAll(".accordion button");
      const element = document.getElementById(`accordion-button-${index}`);
      const itemToggle = element.getAttribute("aria-expanded");

      for (let i = 0; i < items.length; i++) {
        items[i].setAttribute("aria-expanded", "false");
      }

      if (itemToggle == "false") {
        element.setAttribute("aria-expanded", "true");
      }
    },
  },

  components: { CompExamples },
};
</script>
