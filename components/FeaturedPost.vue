<template>
  <div class="featured-post wrapper">
    <img class="post-image" src="~assets/217-536x354.jpg" />

    <div class="content">
      <div class="post-header">
        <p>BEST ARTICLES</p>
        <p>JAN 21, 2022</p>
      </div>
      <h2 class="title">
        Looking for a Better Upwork Time Tracker Alternative? Here Are the Best
      </h2>
      <p class="excerpt">
        I recently sent out a survey to Hubstaff customers and asked them what
        problem they solved with our time tracker.…
      </p>
      <div class="post-footer">
        <p>By Dave Nevogt</p>
        <p>6 min read</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.featured-post {
  display: grid;
  grid-template-columns: 6fr 3fr;
  gap: 90px;
}

.post-image {
  width: 100%;
  height: 440px;
  object-fit: cover;
}

.content {
  border-bottom: solid 3px black;
  display: flex;
  flex-wrap: wrap;

  & > * {
    width: 100%;
  }
}

.post-header {
  display: flex;
  margin-bottom: 20px;
}

.title {
  font-size: 34px;
  margin-bottom: 30px;
  font-weight: 600;
  //   text-decoration: underline;
  line-height: 1.2;
}

.excerpt {
  font-size: 18px;
  line-height: 1.45;
  margin-bottom: 20px;
}

.post-footer {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}
</style>