<template>
  <header
    class="subheader"
    :class="visible ? 'visible' : ''"
    :aria-hidden="visible.toString()"
  >
    <div class="subheader-inner">
      <div class="link-list">
        <ul class="link-primary">
          <li>Remote</li>
          <li>Project Management</li>
          <li>Field Services</li>
        </ul>
        <ul class="link-secondary">
          <li>Productivity</li>
          <li>Time Management</li>
          <li>Tools</li>
        </ul>
      </div>

      <div class="search">Search</div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    handleScroll: function () {
      if (window.scrollY === 0) {
        this.visible = false;
        return;
      }
      this.visible = true;
    },
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
  background-color: white;
  border-bottom: solid 1px #e9e9e9;
  opacity: 0;
  transform: translateY(-100%);
  transition: opacity 0.3s, transform 0.3s;

  &.visible {
    transform: translateY(0);
    opacity: 1;
  }
}

.subheader-inner {
  display: flex;
  height: 50px;
  max-width: 1460px;
  margin-left: auto;
  margin-right: auto;
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
    cursor: pointer;

    &:hover {
      color: #0097ff;
    }
  }
}

.link-primary {
  padding-right: 15px;
  border-right: solid 1px #e9e9e9;

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