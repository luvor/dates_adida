<!-- rename to [...slug].vue -->
<template>
  <div>
    <p>{{ $route.params }}</p>
    <div v-if="post">
      <h1>{{ post.title }}</h1>
      <p>{{ post.date }}</p>
    </div>
    <div v-if="posts">
      <div v-for="post in posts" :key="post.title">
        <NuxtLink :to="`/${post.date}`">{{ post.title }}</NuxtLink>
      </div>
    </div>
  </div>
</template>
<script>
import { data } from "~~/mock";
export default defineComponent({
  data() {
    return {
      date: {
        year: null,
        month: null,
        day: null,
      },
      post: undefined,
      posts: undefined,
      data: undefined,
    };
  },
  mounted() {
    this.data = data;
    this.date = {
      year: this.$route.params.slug[0],
      month: this.$route.params.slug[1],
      day: this.$route.params.slug[2],
    };
    this.fetchPost(this.date);
  },
  methods: {
    fetchPost(date) {
      const res = this.data.filter(
        (item) =>
          (item.date.split("/")[0] == date.year &&
            item.date.split("/")[1] == date.month) ||
          item.date.split("/")[0] == date.year
      );
      if (res.length > 1) {
        this.posts = res;
      } else {
        this.post = res[0];
      }
    },
  },
});
</script>
