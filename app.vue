<template>
  <nav v-if="data" class="flex flex-col p-4">
    <NuxtLink
      class="text-blue-400 decoration-none p-2 cursor-pointer hover:bg-gray-50"
      v-for="item in data"
      :to="`/date/${item.date}`"
      >{{ item.date }}</NuxtLink
    >
  </nav>
  <NuxtPage />
</template>
<script>
import { data } from "./mock";
export default defineComponent({
  components: {},
  data() {
    return {
      data: undefined,
    };
  },
  mounted() {
    this.data = data;
  },
});
</script>
