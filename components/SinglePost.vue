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
    <img class="thumbnail" :alt="article.title" :src="article.thumbnail" />

    <div class="content">
      <div class="post-header">
        <p class="category">{{ article.category }}</p>
        <p class="date" v-if="isFeatured">Date</p>
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
  name: "SinglePost",
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
  },
};
</script>

<style lang="scss" scoped>
.featured-post {
  display: grid;
  grid-template-columns: 1fr;
  margin-bottom: 40px;
  gap: 30px;

  @media (min-width: 1024px) {
    gap: 90px;
    grid-template-columns: 6fr 3fr;
  }

  &.wrapper {
    padding-left: unset;
    padding-right: unset;

    @media (min-width: 1024px) {
      padding-left: 4rem;
      padding-right: 4rem;
    }
  }

  .thumbnail {
    height: 230px;
    object-fit: cover;

    @media (min-width: 1024px) {
      height: 440px;
    }
  }

  .post-header {
    margin-bottom: 20px;
    justify-content: flex-start;
    gap: 20px;

    .category {
      margin-bottom: 0;
    }
  }

  .content {
    border-bottom: solid 3px $dark;
    display: flex;
    flex-wrap: wrap;
    padding-left: 1rem;
    padding-right: 1rem;

    @media (min-width: 1024px) {
      padding-left: 0;
      padding-right: 0;
    }

    & > * {
      width: 100%;
    }
  }

  .title {
    font-size: 24px;
    margin-bottom: 30px;

    @media (min-width: 1024px) {
      font-size: 34px;
    }
  }

  .excerpt {
    display: none;

    @media (min-width: 1024px) {
      display: block;
    }
  }
}

.recent-post {
  .content {
    min-height: unset;
  }

  .title {
    text-transform: none;
    @media (min-width: 1024px) {
      font-size: 24px;
    }
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
  grid-template-rows: 0.5fr 2fr 0.5fr;

  @media (min-width: 1024px) {
    grid-template-rows: 1fr 1.5fr 1fr;
  }
}

.post-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.category,
.date {
  font-size: 12px;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.title {
  font-size: 22px;
  font-weight: 600;
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