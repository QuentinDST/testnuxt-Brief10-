<script>
export default {
  name: 'IndexPage',
  components: {

  }
}



</script>

<template>
  <main>
    <div class="container">
      <div class="row text-center mt-5 homepage">
        <div class="col-12 homepage--content">
          <H2>FIND ALL YOUR STAR WARS FAVORITES CHARACTERS HERE</H2>
          <div class="button-container">
            <Btn class="btn-listing" url="/characters/" text="EXPLORE" />
            <Btn class="btn-listing-2" url="/contact" text="JOIN US" />
          </div>
        </div>
      </div>
    </div>

    <div class="row slider1">
    </div>

    <div class="row slider2">
    </div>

  </main>
</template>



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

.slider1{
  background: url('~assets/images/starwars3.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  width: 100vw;
  height: 650px;
  box-shadow: 0px 0px 20px #fff, 0px 0px 30px #fff, 0px 0px 40px #fff, 0px 0px 50px #474848, 0px 0px 80px #474848, 0px 0px 90px #474848, 0px 0px 100px #474848, 0px 0px 100px #474848;
}

.slider2{
  background: url('~assets/images/darkvador.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  width: 100vw;
  height: 650px;
  box-shadow: 0px 0px 20px #fff, 0px 0px 20px #fff, 0px 0px 25px #fff, 0px 0px 30px #ffdd00, 0px 0px 40px #ffdd00, 0px 0px 50px #e7b811, 0px 0px 55px #e7b811, 0px 0px 100px #fff;
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
