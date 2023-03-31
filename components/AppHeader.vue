<script>
</script>

<template>
    <header>
        <nav class="navbar">
            <ul class="navbar-left">
                <li>
                    <NuxtLink to="/reseau">FILMS</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/characters">CHARACTERS</NuxtLink>
                </li>
            </ul>
            <NuxtLink class="navbar-logo" to="/"><logo/></NuxtLink>
            <div class="navbar-right">
                <form class="navbar-search">
                    <input type="text" placeholder="Dark Vador...">
                </form>
            </div>
        </nav>
    </header>
</template>

<style scoped>

@import url('https://fonts.cdnfonts.com/css/lab-sans-pro');
.navbar {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  background: url('~assets/images/starwars.jpg');
  padding: 20;
  
}

.navbar-left {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 33.33%;
  margin-bottom: 0;
}

.navbar-left li {
  list-style: none;
  margin-right: 20px;
}

.navbar-left li:last-child {
  margin-right: 0;
}

.navbar-logo {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 33.33%;
}

.navbar-right {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 33.33%;
}

.navbar-search{
  order: 2;
}
.navbar-search input {
  background-color: black;
  border: 2px solid rgb(231, 181, 41);
  border-radius: 10px;
  padding: 4px;
  width: 300px;
  transition: all 0.1s ease-out;
}
.navbar-search input:hover {
  border: 2px solid white;
  box-shadow: 0px 0px 2px #fff, 0px 0px 4px #fff, 0px 0px 6px #fff, 0px 0px 8px #a4a39d, 0px 0px 10px #b9b7a9, 0px 0px 12px #dcd4b5, 0px 0px 16px #d6b73c, 0px 0px 20px #fff;
}

a{
    font-family: 'Lab Sans Pro', sans-serif;
    font-size:30px;
    font-weight: bold;
    color: white;
    text-decoration: none;
    transition: all 0.1s ease-out;
}

.navbar-left a:hover {
    border-bottom: 3px solid rgb(231, 181, 41);
    padding-bottom: 5px;
}

@media screen and (max-width: 900px) {
  .navbar {
    height: auto;
  }
  .navbar-left, .navbar-logo, .navbar-right {
    width: 100%;
    text-align: center;
  }
  .navbar-left {
    flex-direction: column;
    padding-left: 0;
    order: 3;
  }
  .navbar-left li {
    margin-right: 0;
    margin-bottom: 10px;
  }
  .navbar-logo {
    order: 1;
    margin-bottom: 20px;
  }
  .navbar-search {
    margin-top: 20px;
    margin-bottom: 20px;
    order: 1;
  }
}

</style>