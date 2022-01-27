<template>
  <footer class="footer">
    <div class="footer-inner wrapper">
      <div class="links">
        <div
          v-for="(section, index) in footer.linksSections"
          :key="index"
          class="link-column"
        >
          <p class="column-title">{{ section.title }}</p>

          <ul>
            <li
              v-for="(link, index) in section.links"
              :key="index"
              class="link"
            >
              {{ link.link }}
            </li>
          </ul>
        </div>
      </div>

      <div class="get-started">
        <p class="title">{{ footer.title }}</p>
        <button class="button button--primary">{{ footer.cta.title }}</button>

        <div class="extra-info">
          <p class="copywrite">{{ footer.copywrite }}</p>
          <div class="social-media">Icons</div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      footer: {
        cta: {},
      },
    };
  },
  async fetch() {
    this.footer = await this.$content("config/footer").fetch();
  },
};
</script>

<style lang="scss" scoped>
.footer {
  padding: 110px 0;
  background-color: #263f54;
  color: $light;

  &-inner {
    display: grid;
    grid-template-columns: 1fr;
    gap: 30px;
    @media (min-width: 1024px) {
      grid-template-columns: 3fr 1fr;
    }
  }
}

.links {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;

  @media (min-width: 1024px) {
    gap: 100px;
    flex-direction: row;
  }

  li {
    margin-bottom: 25px;
    font-size: 12px;
  }
}

.column-title {
  margin-bottom: 50px;
  font-size: 13px;
  font-weight: bold;
}

.get-started {
  height: 100%;
  display: flex;
  flex-direction: column;
  min-height: 250px;

  .title {
    font-size: 26px;
    font-weight: bold;
    margin-bottom: 50px;
  }

  .button {
    padding: 9px 26px;
    font-size: 13px;
    font-weight: 700;
    width: fit-content;
  }

  .extra-info {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    color: rgba(255, 255, 255, 0.5);
    font-size: 13px;
  }

  .copywrite {
    border-bottom: 1px solid rgba(255, 255, 255, 0.5);
    padding-bottom: 15px;
    margin-bottom: 15px;
  }
}
</style>