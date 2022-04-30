<template>
  <Banner />

  <div class="bg-rose-50">
    <Row
      title="Netflix Originals"
      :url="request.fetchNetflixOriginals"
      :isLarge="true"
    ></Row>
    <Row title="Netflix Hindi" :url="request.fetchNetflixHindi"></Row>
    <Row title="Netflix Originals" :url="request.fetchNetflixOriginals"></Row>
    <Row title="Netflix Hindi" :url="request.fetchNetflixHindi"></Row>
  </div>
</template>

<script setup>
import Row from "./components/row.vue";
import Banner from "./components/banner.vue";
import request from "./constant";
</script>
