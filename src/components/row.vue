<template>
  <div class="w-full px-4 md:pl-[45px] py-2">
    <div>
      <h2 class="text-white font-semibold text-2xl py-5">{{ title }}</h2>
    </div>
    <div class="poster_row flex gap-3 md:gap-4 overflow-x-auto">
      <img
        v-for="movie in movies"
        :key="movie.id"
        :src="
          IMG.cdnURL +
          IMG.baseURL +
          [isLarge ? movie.poster_path : movie.backdrop_path] +
          IMG.transformIMG
        "
        :alt="movie.title"
        :class="[isLarge ? 'h-[250px] rounded' : 'h-[125px] rounded']"
      />
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import instance from "../axios";
import { IMG } from "../constant";

const props = defineProps({
  title: String,
  url: String,
  isLarge: {
    type: Boolean,
    default: false,
  },
});

const { title, url, isLarge } = props;
const movies = ref(null);

async function fetchData() {
  const response = await instance.get(url);
  movies.value = response.data.results;
}

onMounted(() => {
  fetchData();
});
</script>

<style scoped>
.poster_row::-webkit-scrollbar {
  display: none;
}
</style>
