<template>
  <div>
    <FeaturedPost />
    <div class="featured-articles">
      <div class="wrapper">
        <h5>Featured Articles</h5>

        <div class="featured-articles-inner">
          <SinglePost
            v-for="article in articles"
            :key="article.key"
            :article="article"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FeaturedPost from "~/components/FeaturedPost";
import SinglePost from "~/components/SinglePost";

export default {
  name: "IndexPage",
  components: { FeaturedPost, SinglePost },
  data() {
    return {
      articles: [
        {
          id: 1,
          title: "test 1",
          thumbnail: "How-to-pay-freelance",
          excerpt: "Test",
          category: "Best Articles",
          date: "01/21/22",
          estimatedTime: "6 min",
        },
        {
          id: 2,
          title: "The 11 Top Time Tracking Apps for Mac",
          thumbnail: "Mac-time-tracking-apps",
          //   excerpt: "Test",
          category: "Best Articles",
          date: "01/6/22",
          estimatedTime: "13 min",
        },
        {
          id: 3,
          title: "A Guide to Paying Independent Contractors & Remote Employees",
          thumbnail: "Upwork-competitors",
          excerpt: "Test",
          category: "Outsourcing",
          date: "08/25/21",
          estimatedTime: "7 min",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.featured-articles {
  background-color: #fafafa;

  &-inner {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10%;
  }
}
</style>
