<template>
  <div>
    <div v-if="posts">
      <div v-for="post in posts">
        <div class="p-4 bg-gray-50 rounded-md">
          <h2>{{ post.title }}</h2>
          <p>{{ post.date }}</p>
        </div>
      </div>
    </div>
    <div v-else>
      <h2>Не найдено</h2>
    </div>
  </div>
</template>
<script>
import { data } from "./../../../mock.js";
export default defineComponent({
  data() {
    return {
      posts: null,
    };
  },
  mounted() {
    const date = this.$route.params;
    this.posts = data.filter((post) => post.date.split("/")[0] == date.year);
  },
});
</script>
