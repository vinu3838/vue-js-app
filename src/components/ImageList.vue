<template>
  <div v-if="isLoggedIn" class="image-container">
    <img v-for="(image, index) in allImages" :src="image.link" :key="index" />
  </div>
  <h2 v-else>
      Log in to get started
  </h2>
</template>
<script>
import { mapActions, mapGetters } from "vuex";
export default {
  name: "ImageList",
  methods: {
    ...mapActions(["fetchImages"]),
  },
  computed: {
    ...mapGetters(["allImages", "isLoggedIn"]),
  },
  created() {
    this.fetchImages();
  },
};
</script>
<style scoped>
.image-container {
  column-count: 3;
  column-gap: 0; 
  display: grid;
  grid-template-columns:1fr 1fr 1fr 1fr 1fr;


  
}
img {
  max-width: 100%;
  padding: 5px;
}
</style>