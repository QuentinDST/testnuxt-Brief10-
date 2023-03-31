<template>
    <div class="home-button">
    <NuxtLink :to="url" class="home-button-link"> 
      <span class="home-button-text">{{ text }}</span>
    </NuxtLink>
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    },
    url:{
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.home-button {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(231, 181, 41);
  border-radius: 50px;
  width: 350px;
  height: 50px;
  cursor: pointer;
}

.home-button:hover {
  background-color: #f5d042;
  font-weight: lighter;
  box-shadow: 0px 0px 2px #fff, 0px 0px 4px #fff, 0px 0px 6px #fff, 0px 0px 8px #a4a39d, 0px 0px 10px #b9b7a9, 0px 0px 12px #dcd4b5, 0px 0px 16px #86847c, 0px 0px 20px #fff;
}

.home-button-link {
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  width: 100%;
  height: 100%;
}

.home-button-text {
  font-family: 'Lab Sans Pro', sans-serif;
  font-weight: bolder;
  color: black;
  font-size: 30px;
  text-align: center;
}
</style>

