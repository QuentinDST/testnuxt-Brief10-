<template>
    <div>
      <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-height="650"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <!-- SLIDE 1 -->
        <b-carousel-slide :img-src="require('~/assets/images/starwars3.jpg')">
            <h2>CHARACTERS</h2>
        </b-carousel-slide>
  
        <!-- SLIDE 2 -->
        <b-carousel-slide :img-src="require('~/assets/images/darkvador.jpg')">
          <h2>MOVIES</h2>
        </b-carousel-slide>
  
        <!-- SLIDE 3 -->
        <b-carousel-slide :img-src="require('~/assets/images/starwars4.jpg')">
          <h2>PLANET</h2>
        </b-carousel-slide>
  
        <!-- SLIDE 4 -->
        <b-carousel-slide :img-src="require('~/assets/images/kyloren.jpeg')">
           <h2>VEHICULES</h2>
        </b-carousel-slide>
      </b-carousel>
  
      <p class="mt-4">
        Slide #: {{ slide }}<br>
        Sliding: {{ sliding }}
      </p>
    </div>
  </template>
  
  <script>
    export default {
      data() {
        return {
          slide: 0,
          sliding: null
        }
      },
      methods: {
        onSlideStart(slide) {
          this.sliding = true
        },
        onSlideEnd(slide) {
          this.sliding = false
        }
      }
    }
  </script>

<style>

#carousel-1{
    width: 100vw;
    margin: 0 auto; 
    box-shadow: 0px 0px 20px #fff, 0px 0px 20px #fff, 0px 0px 25px #fff, 0px 0px 30px #ffdd00, 0px 0px 40px #ffdd00, 0px 0px 50px #e7b811, 0px 0px 55px #e7b811, 0px 0px 100px #fff;
}
</style>