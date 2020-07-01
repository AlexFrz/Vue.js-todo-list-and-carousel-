<template>
  <div id="app">
    <carousel>
      <carousel-slide v-for="n in slides" :index="n - 1">
        <div
          style="position:absolute; left:0; right:0; text-align:center; top:50%; color:#FFF; font-size:16px;"
        >Slide {{ n }}</div>
        <img :src="'https://loremflickr.com/600/300/' + n" width="100%" />
      </carousel-slide>
    </carousel>
    <button @click="addSlide">Ajouter un slide</button>
    <button @click="removeSlide">Supprimer un slide</button>

    <todos></todos>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Carousel from "./components/carousel/Carousel";
import CarouselSlide from "./components/carousel/CarouselSlide";

export default {
  data() {
    return {
      slides: 5
    };
  },
  methods: {
    addSlide() {
      this.slides++;
    },
    removeSlide() {
      this.slides--;
    }
  },
  components: {
    Todos,
    Carousel,
    CarouselSlide
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
</style>
