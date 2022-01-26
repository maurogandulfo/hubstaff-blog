<template>
  <article class="article">
    <img
      class="thumbnail"
      :src="require(`~/assets/images/${article.thumbnail}.png`)"
    />

    <div class="content">
      <p class="category">{{ article.category }}</p>
      <h3 class="title">
        {{ article.title }}
      </h3>

      <div class="article-footer">
        <p>
          {{
            new Date(article.date).toLocaleDateString("en-us", {
              year: "numeric",
              month: "short",
              day: "numeric",
            })
          }}
        </p>
        <p>{{ article.estimatedTime }} read</p>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  props: {
    article: Object,
  },
};
</script>

<style lang="scss" scoped>
.thumbnail {
  width: 100%;
  margin-bottom: 10px;
}

.content {
  min-height: 200px;
  display: grid;
  grid-template-rows: 1fr 3fr 1fr;

  //   & > * {
  //     width: 100%;
  //   }
}

.category {
  font-size: 12px;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.title {
  font-size: 22px;
  font-weight: 600;
}

.article-footer {
  align-items: center;
  display: flex;
  justify-content: space-between;
}
</style>