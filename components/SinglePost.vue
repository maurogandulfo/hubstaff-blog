<template>
  <article
    class="article"
    :class="
      isFeatured
        ? 'featured-post wrapper'
        : '' + isRecent
        ? 'recent-post wrapper'
        : ''
    "
  >
    <img class="thumbnail" :src="article.thumbnail" />

    <div class="content">
      <div class="post-header">
        <p class="category">{{ article.category }}</p>
        <p v-if="isFeatured">{{ getFormatedDate(article.date) }}</p>
      </div>

      <h3 class="title">
        {{ article.title }}
      </h3>

      <p v-if="isFeatured" class="excerpt">
        {{ article.shortExcerpt }}
      </p>

      <div class="article-footer">
        <p>{{ article.estimatedTime }} read</p>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  props: {
    article: {},
    isFeatured: {
      type: Boolean,
      default: false,
    },
    isRecent: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    getFormatedDate: function (date) {
      return new Date(date).toLocaleDateString("en-us", {
        year: "numeric",
        month: "short",
        day: "numeric",
      });
    },
    getArticleExcerpt: function (articleContent) {
      console.log(articleContent);
      if (!articleContent) return;
      return String(articleContent).split(".")[0];
    },
  },
};
</script>

<style lang="scss" scoped>
.featured-post {
  display: grid;
  grid-template-columns: 1fr;
  gap: 90px;
  margin-bottom: 40px;

  &.wrapper {
    padding-left: unset;
    padding-right: unset;
  }

  @media (min-width: 768px) {
    grid-template-columns: 6fr 3fr;
  }

  .thumbnail {
    height: 440px;
    object-fit: cover;
  }

  .post-header {
    margin-bottom: 20px;

    .category {
      margin-bottom: 0;
    }
  }

  .content {
    border-bottom: solid 3px black;
    display: flex;
    flex-wrap: wrap;
    padding-left: 2rem;
    padding-right: 2rem;

    & > * {
      width: 100%;
    }
  }

  .title {
    font-size: 34px;
    margin-bottom: 30px;
  }
}

.recent-post {
  .content {
    min-height: unset;
  }

  .article-footer {
    margin-bottom: 0;
  }
}

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

.post-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.category {
  font-size: 12px;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.title {
  font-size: 22px;
  font-weight: 600;
  //   background-image: linear-gradient(currentColor, currentColor);
  //   background-position: 0% 100%;
  //   background-repeat: no-repeat;
  //   background-size: 0% 2px;

  //   &:hover {
  //     background-size: 100% 2px;
  //   }
}

.excerpt {
  font-size: 18px;
  line-height: 1.45;
  margin-bottom: 20px;
}

.article-footer {
  align-items: center;
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
  font-size: 12px;
}
</style>