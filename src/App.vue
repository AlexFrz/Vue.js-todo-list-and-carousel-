<template>
  <div id="app">
    <carousel>
      <carousel-slide>Salut les gens</carousel-slide>
      <carousel-slide>Aurevoir les gens</carousel-slide>
    </carousel>
    <todos></todos>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Carousel from "./components/carousel/Carousel";
import CarouselSlide from "./components/carousel/CarouselSlide";

export default {
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
