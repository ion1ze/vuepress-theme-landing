<template>
  <div class="layout">
    <ParentLayout />
    <footer>
      <p>
        <a
          v-if="config.footer.icp"
          href="https://beian.miit.gov.cn/"
          target="_blank"
        >
          {{ config.footer.icp || "" }}
        </a>
        {{ config.footer.police || "" }}
      </p>
      <p v-if="config.footer.copyright">&copy;{{ config.footer.copyright }}</p>
    </footer>
  </div>
</template>

<script>
import ParentLayout from "@parent-theme/layouts/Layout.vue";
export default {
  name: "Layout",
  components: {
    ParentLayout,
  },
  computed: {
    config() {
      return this.$site.themeConfig;
    },
  },
};
</script>

<style lang="stylus">
footer {
  text-align: center;
}
</style>