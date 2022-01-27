<template>
  <div class="header-container">
    <header class="header">
      <div class="header-inner">
        <img class="logo" :src="header.logo" />

        <div class="products link">{{ header.productDropdown }}</div>

        <div class="learn-more">
          <button class="button button--primary">
            {{ header.cta.title }}
          </button>
        </div>

        <div class="sing-in link">{{ header.actionsDropdown }}</div>
      </div>
    </header>

    <SubHeader />
  </div>
</template>

<script>
import SubHeader from "./SubHeader";

export default {
  components: { SubHeader },
  data() {
    return {
      header: {
        cta: {},
      },
    };
  },
  async fetch() {
    this.header = await this.$content("config/header").fetch();
  },
};
</script>

<style lang="scss" scoped>
.header-container {
  width: 100%;
  position: fixed;
  top: 0;
  z-index: 10;
}

.header {
  border-bottom: solid 1px #e9e9e9;
  z-index: 1;
  background: white;
  position: relative;
}

.header-inner {
  display: grid;
  grid-template-columns: 170px 1fr 1fr 85px;
  height: 70px;
  align-items: center;
  max-width: 1460px;
  margin-left: auto;
  margin-right: auto;
}

.logo {
  max-width: 150px;
}

.products {
  display: flex;
  justify-content: flex-start;
}
.learn-more {
  display: flex;
  justify-content: flex-end;
}

.sing-in {
  text-align: center;
}
</style>