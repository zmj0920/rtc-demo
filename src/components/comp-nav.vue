<!--
 * @Description: 导航栏组件
 * @Date: 2022-03-09 16:47:13
 * @LastEditTime: 2022-03-18 12:06:18
-->
<template>
  <div class="nav-container">
    <div class="right-region">
      <img v-if="isZhLang" class="logo" src="https://web.sdk.qcloud.com/trtc/webrtc/assets/logo/trtc-logo-cn-w.png" />
      <img v-if="isEnLang" class="logo" src="https://web.sdk.qcloud.com/trtc/webrtc/assets/logo/trtc-logo-en-w.png" />
    </div>
    <div class="left-region">
      <span class="language" @click="toggleLanguage">
        <svg-icon icon-name="language"></svg-icon>
      </span>
      <span class="github" @click="goToGithub">
        <svg-icon icon-name="github" className="github-svg"></svg-icon>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'navContainer',
  data() {
    return  {
    };
  },
  computed: {
    isZhLang() {
      return this.$i18n.locale === 'zh';
    },
    isEnLang() {
      return this.$i18n.locale === 'en';
    },
  },
  methods: {
    toggleLanguage() {
      switch (this.$i18n.locale) {
        case 'en':
          this.$i18n.locale = 'zh';
          localStorage.setItem('trtc-quick-vue2-language', 'zh');
          break;
        case 'zh':
          this.$i18n.locale = 'en';
          localStorage.setItem('trtc-quick-vue2-language', 'en');
          break;
      }
      document.title = this.$i18n.t('title');
    },
    goToGithub() {
      window.open('https://github.com/LiteAVSDK/TRTC_Web', '_blank');
    },
  },
};
</script>

<style lang="scss" scoped>
.nav-container{
  width: 100%;
  height: 60px;
  padding: 10px 10px;
  background-color: #00182F;
  display: flex;
  justify-content: space-between;
  color: #ffffff;
  .right-region {
    .logo {
      height: 100%;
    }
  }
  .left-region {
    height: 100%;
    display: flex;
    align-items: center;
    cursor: pointer;
    .github {
      margin-left: 20px;
      cursor: pointer;
      .github-svg {
        width: 40px;
        height: 40px;
      }
    }
  }
}
</style>
