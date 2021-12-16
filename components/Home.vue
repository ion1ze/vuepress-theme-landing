<template>
  <main class="home">
    <div class="hero">
      <div class="content">
        <h1 v-if="data.heroTitle !== null">
          {{ data.heroTitle || $title || "Hello" }}
        </h1>
        <p v-if="data.heroSubtitle !== null">
          {{ data.heroSubtitle || $description || "Welcome to my site." }}
        </p>
      </div>
      <div class="screenshot">
        <img :src="$withBase(data.screenshot)" alt="screenshot" />
      </div>
      <div class="actions">
        <NavLink
          class="action-button"
          v-for="action in data.actions"
          :key="action.link"
          :item="action"
        />
      </div>
    </div>
    <Content />
  </main>
</template>

<script>
import NavLink from "@parent-theme/components/NavLink.vue";
export default {
  name: "Home",
  components: {
    NavLink,
  },
  computed: {
    data() {
      return this.$page.frontmatter;
    },
  },
};
</script>

<style lang="stylus">
.home {
  padding: $navbarHeight 1.5rem;
  max-width: $homePageWidth;
  margin: 0px auto;
  display: block;

  .hero {
    text-align: center;
    padding: 80px 0;

    .screenshot {
      img {
        max-width: 100%;
      }
    }

    .actions {
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
      padding: 20px 0;

      & > * {
        margin: 0 16px;
      }

      .action-button {
        display: inline-block;
        font-size: 1rem;
        padding: 0.6rem 1.2rem;
        color: #fff;
        background-color: $accentColor;
        border-radius: 4px;
        transition: background-color 0.1s ease;
        box-sizing: border-box;
        border-bottom: 1px solid darken($accentColor, 10%);

        &:hover {
          background-color: lighten($accentColor, 10%);
        }

        & svg {
          color: #fff;
        }

        @media screen and (min-width: 1024px) {
          font-size: 1.2rem;
          padding: 0.8rem 1.6rem;
        }
      }
    }
  }

  img {
    max-width: 100%;
  }
}
</style>