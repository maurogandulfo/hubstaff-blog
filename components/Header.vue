<template>
  <header class="header-container">
    <div class="header">
      <div class="header-inner wrapper">
        <img class="logo" alt="hubstaff-logo" :src="header.logo" />

        <div class="products link">{{ header.productDropdown }}</div>

        <div class="learn-more">
          <button class="button button--primary">
            {{ header.cta.title }}
          </button>
        </div>

        <div class="sing-in link">{{ header.actionsDropdown }}</div>

        <div class="menu-toggle">Menu Icon</div>
      </div>
    </div>

    <SubHeader />
  </header>
</template>

<script>
import SubHeader from "./SubHeader";

export default {
  name: "Header",
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
  border-bottom: solid 1px $light-gray;
  z-index: 1;
  background: $light;
  position: relative;
}

.header-inner {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  height: 70px;
  align-items: center;

  @media (min-width: 1024px) {
    grid-template-columns: 170px 1fr 1fr 85px;
  }
}

.logo {
  max-width: 150px;
}
.products,
.learn-more,
.sing-in {
  display: none;

  @media (min-width: 1024px) {
    display: flex;
  }
}

.products {
  justify-content: flex-start;
}
.learn-more {
  justify-content: flex-end;
}

.sing-in {
  justify-content: center;
}

.menu-toggle {
  display: flex;
  justify-content: flex-end;

  @media (min-width: 1024px) {
    display: none;
  }
}
</style>