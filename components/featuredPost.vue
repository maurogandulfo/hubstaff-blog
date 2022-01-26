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
  //   name: "FeaturedPost",
};
</script>

<style lang="scss">
</style>