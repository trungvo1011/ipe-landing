<template>
  <div class="certifications" id="Certifications">
    <div class="certifications__container containerr">
      <Title
        title="Certifications"
        descrip="엄격한 성능 검증으로 고품질의 서비스 제공을 위해 노력합니다."
        color="#fff"
      />
      <div class="cardd exmodule">
        <div class="front" v-for="(item, index) in data" :key="index">
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
@import "../assets/stylesheets/certifications.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script>
import Banner1 from "../assets/images/certifications1.svg";
import Banner2 from "../assets/images/certifications2.svg";
import Banner3 from "../assets/images/certifications3.svg";
export default {
  data() {
    return {
      data: [
        {
          background: Banner1,
          img: "TTA 시험 인증",
          text_1:
            "한국정보통신기술협회(TTA)의 ‘공공기관용 보안인증’을 획득했습니다. 공공기관용 보안 인증은 잇따른 IP 카메라 해킹으로 CCTV 카메라에 대한 보안 강화 필요성이 지속 제기되자 정부 차원에서 보안",
        },
        {
          background: Banner2,
          img: "KISA 인증",
          text_1:
            "아이피에딧 드래프트는 정보보안과 품질관리를 가장 소중히 생각하여 정보보안 관리시스템 IOS/IEC 27001:2013 품질관리시스템 ISO9001:2015 인증을 획득하였습니다.",
        },
        {
          background: Banner3,
          img: "ISO 인증",
          text_1:
            "아이피에딧 드래프트는 정보보안과 품질관리를 가장 소중히 생각하여 정보보안 관리시스템 IOS/IEC 27001:2013와 품질관리시스템 ISO9001:2015 인증을 획득하였습니다. 또한",
        },
      ],
    };
  },
  components: {},
};
</script>