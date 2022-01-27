<template>
  <div class="cta">
    <span class="cta-decoration"></span>
    <div class="cta-inner wrapper">
      <h3 class="title">{{ cta.title }}</h3>

      <!-- <nuxt-content :document="{ body: 'cta.content' }" /> -->
      <!-- <p class="content">
      </p> -->
      <button class="button">{{ cta.url }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cta",
  props: { cta: Object },
  mounted() {
    //Fix this
    console.log(this.cta);
  },
};
</script>

<style lang="scss">
.cta {
  overflow: hidden;
  color: $light;
  position: relative;
  background-color: #294dff;
  min-height: 600px;
  background-image: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNzgycHgiIGhlaWdodD0iMTIyMnB4IiB2aWV3Qm94PSIwIDAgNzgyIDEyMjIiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CiAgICA8dGl0bGU+RWxsaXBzZSAyPC90aXRsZT4KICAgIDxnIGlkPSJQYWdlLTEiIHN0cm9rZT0ibm9uZSIgc3Ryb2tlLXdpZHRoPSIxIiBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGZpbGwtb3BhY2l0eT0iMC4xIj4KICAgICAgICA8ZyBpZD0iSFMtaG9tZS1wYWdlLXJlZnJlc2gtMjAyMF90ZXN0IiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMzcyLjAwMDAwMCwgLTY1NTYuMDAwMDAwKSIgZmlsbD0iI0ZGRkZGRiI+CiAgICAgICAgICAgIDxwYXRoIGQ9Ik02MzMuNDY4NzgsNjc5MS4wMDU1NiBDNjEyLjU4NDg2Miw2ODAzLjczMTkxIDYwMy41ODIzMDksNjgzMC42Mzk3OSA2MTIuMDAwOTE4LDY4NTQuNjQ2MTQgQzYzNy44NTYwMjksNjkyOC4zMjI1NiA2MzMuNzU4MTk1LDcwMTMuMjE5OTUgNTkzLjc0MDE0NSw3MDg2LjUxMjY1IEM1NTMuNzcyMjA2LDcxNTkuNzcxNDEgNDg2LjIwODU3NSw3MjA1LjU2NTg4IDQxMy4yNzksNzIxOC4xNjUzIEMzODkuNTA2MDQzLDcyMjIuMjY2NzIgMzcyLDcyNDMuODY0NDYgMzcyLDcyNjkuNTEwNDggQzM3Miw3MzcyLjkzMTQgMzcyLjAxNDMxNyw3NjE3LjAwOTE4IDM3Mi4wMTQzMTcsNzcyNS43MzI4NiBDMzcyLjAxNDMxNyw3NzU1LjY1Mjk4IDM5NS42MTAzNTMsNzc3OS44Mjc1NyA0MjMuNjQ4ODYxLDc3NzcuODkxMjQgQzUzNi41MzIwNTcsNzc3MC4xNzk4NyA2NDIuODU0ODMzLDc3MzYuODAzMjkgNzM3LjY3MjU4Niw3NjgzLjQyNTg1IEw3ODMuMjE3MTM4LDc2NTUuNjY2MzkgQzc5NS42MTY5OTYsNzY0Ny41MzE0NSA4MDcuNzc0NDgyLDc2MzkuMDI0NTkgODE5LjY5MzY4Niw3NjMwLjE1NjE1IEM4MzMuNjg5OTMsNzYxOS43NjMxNCA4MzkuODc0MDA4LDc2MDEuMDUzNjYgODM0Ljg5ODcyNCw3NTgzLjY4NDI2IEM4MDQuNzE3NzI1LDc0NzguMjg3MTYgODE0LjA2MDgyNyw3MzYwLjQwODcyIDg3MC4xNTcyNzQsNzI1Ny42Mjk4MSBDOTI2LjUwNTI5OCw3MTU0LjM1MjA1IDEwMTguNjkxNzIsNzA4Ny4xODU2NSAxMTIwLjIwMTgyLDcwNjMuMjQyNzYgQzExMzYuNDg5ODcsNzA1OS40MjMyNCAxMTQ5LjAwMTIsNzA0NS4wODgyMSAxMTUwLjU3OTE3LDcwMjcuNDE0NzggQzExNTIuNDU0NzUsNzAwNi41MDc3NCAxMTUzLjU5NCw2OTg1LjM4MDggMTE1My45NzEzNyw2OTY0LjAzOTg2IEwxMTU0LDY5MzEuODIxODMgQzExNTEuODcxODMsNjgwNy41NzIxIDExMjQuMTc3OTYsNjY5MC4wMjU3MiAxMDc2LjI3NzE4LDY1ODQuODE5MDIgQzEwNjQuMDE2NCw2NTU3Ljg3Mjc2IDEwMzIuNDkxNjIsNjU0OC4wODE5IDEwMDguMDY5MjYsNjU2Mi45MzM0OCBMNjMzLjQ2ODc4LDY3OTEuMDA1NTYgWiIgaWQ9IkVsbGlwc2UtMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNzYzLjAwMDAwMCwgNzE2Ny4wMDAwMDApIHNjYWxlKC0xLCAxKSB0cmFuc2xhdGUoLTc2My4wMDAwMDAsIC03MTY3LjAwMDAwMCkgIj48L3BhdGg+CiAgICAgICAgPC9nPgogICAgPC9nPgo8L3N2Zz4=);
  background-position: 30% 43%;
  background-repeat: no-repeat;
  background-size: 120%;
  display: flex;
  align-items: center;

  &-decoration {
    background: $light;
    border-radius: 50%;
    top: -100px;
    content: "";
    display: block;
    height: 200px;
    position: absolute;
    width: 150%;
    left: -25%;

    @media (min-width: 1024px) {
      width: 130%;
      left: -15%;
    }
  }

  &-inner {
    text-align: center;
    //temp
    margin-top: 100px;
  }

  .title {
    font-size: 46px;
    font-weight: 700;
    margin-bottom: 50px;
  }

  .content {
    font-size: 18px;
    line-height: 1.5;
    margin-bottom: 40px;
  }

  .button {
    background-color: $dark-blue;
    font-size: 20px;
    color: $light;
    padding: 23px 32px;
    font-weight: 700;
    border-radius: 8px;
  }
}
</style>
