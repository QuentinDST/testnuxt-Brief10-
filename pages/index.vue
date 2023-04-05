<template>
  <main>
    <div class="container">
      <div class="row text-center mt-5 homepage">
        <div class="col-12 mt-5 homepage--content">
          <H2>FIND ALL YOUR STAR WARS FAVORITES CHARACTERS HERE</H2>
          <div class="button-container">
            <Btn class="btn-listing" url="/characters/" text="EXPLORE" />
            <Btn class="btn-listing-2" url="/contact" text="JOIN US" />
          </div>
        </div>
      </div>
    </div>

    <div class="row slider1">
      <slider class="slider--characters"/>
    </div>
    
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  components: {
    swiper: {
      
    }
  },
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

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poller+One&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');


h1{
  margin-bottom: 0;
  color: white;
}

H2{
  font-family: 'Poller One', cursive;
  color: white;
}

.homepage{
  background: url('~assets/images/starwars1.jpg');
  background-repeat: no-repeat;
  background-size: contain;
  height :800px; 
}

.button-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  height: 100%;
}


.btn-listing-2{
  margin-top: 50px;
}

@media screen and (max-width: 770px) {
  .button-container {
    display: flex;
    align-items: center;
  }

  .btn-listing-2{
  margin-top: 30px;
}

  .slider1{
    background-size: cover;
    background-position: center;
  }

  .slider2{
    background-size: cover;
    background-position: center;
  }


}
</style>
