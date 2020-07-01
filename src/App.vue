<template>
  <div id="app">
    <carousel>
      <carousel-slide>
        <div
          style="position:absolute; left:0; right:0; text-align:center; top:50%; color:#FFF; font-size:16px;"
        >Au revoir les gens</div>
        <img src="https://picsum.photos/630/300?grayscale
" width="100%" />
      </carousel-slide>
      <carousel-slide>
        <div
          style="position:absolute; left:0; right:0; text-align:center; top:50%; color:#FFF; font-size:16px;"
        >Au revoir les gens</div>
        <img src="https://picsum.photos/630/300?grayscale
" width="100%" />
      </carousel-slide>
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
