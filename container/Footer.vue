<template>
  <div class="footer">
    <div class="footer__container containerr">
      <div class="content">
        <div class="logo-footer">
          <img :src="Draft" alt="draft" />
        </div>
        <ul>
          <li><a href="https://ipactory.com"> 회사소개</a></li>
          <li><a href="https://ipedit.co">서비스소개</a></li>
          <li><a href="#">이용약관</a></li>
          <li><a href="#">개인정보이용방침</a></li>
        </ul>
      </div>
      <div class="information">
        (주)아이팩토리 | 대표자: 유장현 | 사업자번호: 123-12-12345 |
        통신판매업번호: 123123123 | 서울특별시 서초구 논현로 175 신한빌딩 6층 |
        대표번호: 02-6954-7657 | 이메일 admin@ipactory.com | 개인정보책임자: 000
      </div>
      <div class="years">© 2019 — 2020 IPACTORY. All Rights Reserved</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/footer.scss";
@import "../assets/stylesheets/global.scss";
</style>

<script>
import Logo from "../assets/images/iconFooter.svg";
import Draft from "../assets/images/draft.svg";
export default {
  data() {
    return {
      Draft: Draft,
      logo: Logo,
    };
  },
  components: {},
};
</script>
