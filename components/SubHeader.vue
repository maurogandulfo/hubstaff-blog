<template>
  <div
    class="subheader"
    :class="visible ? 'visible' : ''"
    :aria-hidden="visible.toString()"
  >
    <div class="subheader-inner wrapper">
      <div class="link-list">
        <ul class="link-primary">
          <li
            v-for="(link, index) in subheader.primaryLinks"
            :key="index"
            class="link"
          >
            {{ link.link }}
          </li>
        </ul>
        <ul class="link-secondary">
          <li
            v-for="(link, index) in subheader.secondaryLinks"
            :key="index"
            class="link"
          >
            {{ link.link }}
          </li>
        </ul>
      </div>

      <div class="search">{{ subheader.searchButton }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SubHeader",
  data() {
    return {
      subheader: {},
      visible: true,
      lastPosition: 0,
    };
  },
  methods: {
    handleScroll: function () {
      if (window.innerWidth <= 768) return;

      if (window.scrollY < this.lastPosition || window.scrollY === 0) {
        this.visible = true;
      } else {
        this.visible = false;
      }

      this.lastPosition = window.scrollY;
    },
  },
  async fetch() {
    this.subheader = await this.$content("config/subheader").fetch();
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<style lang="scss" scoped>
.subheader {
  display: none;
  background-color: $light;
  border-bottom: solid 1px $light-gray;
  opacity: 0;
  transform: translateY(-100%);
  transition: opacity 0.3s, transform 0.3s;

  @media (min-width: 1024px) {
    display: block;
  }

  &.visible {
    transform: translateY(0);
    opacity: 1;
  }
}

.subheader-inner {
  display: flex;
  height: 50px;
  justify-content: space-between;
  align-items: center;
}

.link-list {
  display: flex;
  height: 100%;
}

.link-primary,
.link-secondary {
  display: flex;
  gap: 30px;
  align-items: center;

  li {
    font-size: 14px;
    display: flex;
    align-items: center;
    height: 100%;
  }
}

.link-primary {
  padding-right: 15px;
  border-right: solid 1px $light-gray;

  li {
    font-weight: 600;
    border-style: solid;
    border-bottom-width: 3px;

    &:nth-child(1) {
      border-color: #0097ff;
    }

    &:nth-child(2) {
      border-color: #08ba98;
    }

    &:nth-child(3) {
      border-color: #e47c00;
    }
  }
}

.link-secondary {
  margin-left: 15px;
}

.products {
  display: flex;
  justify-content: flex-start;
}
.learn-more {
  display: flex;
  justify-content: flex-end;
}
</style>