<template>
  <div>
    <div class="no-posts" v-if="articles.length === 0">
      <p>Sorry, we don't have articles to show</p>
    </div>
    <div v-else>
      <SinglePost :article="articles[0]" :isFeatured="true" />

      <div class="featured-articles">
        <div class="wrapper">
          <h5 class="title">Featured Articles</h5>

          <div class="featured-articles-inner">
            <SinglePost
              v-for="article in articles"
              :key="article.key"
              :article="article"
            />
          </div>
        </div>
      </div>

      <div class="recent-articles">
        <div class="wrapper">
          <h5 class="title">Recent</h5>

          <div class="recent-articles-inner">
            <SinglePost
              :isRecent="true"
              v-for="article in articles"
              :key="article.key"
              :article="article"
            />
          </div>
        </div>
      </div>
    </div>
    <Cta :cta="cta" />
  </div>
</template>

<script>
import SinglePost from "~/components/SinglePost";
import Cta from "~/components/Cta";

export default {
  components: { SinglePost, Cta },
  data() {
    return {
      articles: {},
      cta: {},
    };
  },
  async fetch() {
    this.articles = await this.$content("articles")
      .sortBy("createdAt", "desc")
      .fetch();

    const { cta } = await this.$content("pages/home").fetch();
    this.cta = cta;
  },
  head() {
    return {
      title: "Hubstaff Blog",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "Learn how to run a remote company more successfully, more profitable and all while having more fun. For remote startup teams, freelancers and virtual teams.",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.no-posts {
  height: 300px;
  justify-content: center;
  display: flex;
  align-items: center;
}

.featured-articles {
  background-color: #fafafa;

  &-inner {
    display: grid;
    grid-template-columns: 1fr;
    gap: 30px;

    @media (min-width: 1024px) {
      grid-template-columns: repeat(3, 1fr);
      gap: 10%;
    }
  }
}

.recent-articles {
  &-inner {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;

    @media (min-width: 1024px) {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .article {
    transition: transform 0.2s ease;
    cursor: pointer;

    &:hover {
      box-shadow: 0 10px 25px 0 rgb(0 0 0 / 10%);
      transform: translateZ(0) translateY(-10px);
    }

    .content {
      padding: 30px;
    }
  }
}
.featured-articles,
.recent-articles {
  padding: 40px 0;

  @media (min-width: 1024px) {
    padding: 100px 0;
  }

  .title {
    font-size: 18px;
    text-transform: uppercase;
    font-weight: bold;
    margin-bottom: 20px;

    @media (min-width: 1024px) {
      font-size: 16px;
      margin-bottom: 40px;
    }
  }

  .article.wrapper {
    width: 100%;
    padding-left: unset;
    padding-right: unset;
  }
}
</style>
