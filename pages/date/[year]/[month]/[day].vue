<template>
  <div>
    <div v-if="post">
      <div class="p-4 bg-gray-50 rounded-md">
        <h2>{{ post.title }}</h2>
        <p>{{ post.date }}</p>
      </div>
    </div>
    <div v-else>
      <h2>Не найдено</h2>
    </div>
  </div>
</template>
<script>
import { data } from "./../../../../mock.js";
export default defineComponent({
  data() {
    return {
      post: null,
    };
  },
  mounted() {
    const date = this.$route.params;
    console.log(`${date.year}/${date.month}/${date.day}`);
    this.post = data.find(
      (post) => post.date == `${date.year}/${date.month}/${date.day}`
    );
  },
});
</script>
