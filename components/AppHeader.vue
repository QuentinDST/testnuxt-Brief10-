
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

      <NuxtLink class="navbar-logo" to="/">
        <logo />
      </NuxtLink>

      <div class="navbar-right">
        <form class="navbar-search" @input="searchCharacters">
          <input type="text" v-model="searchQuery" placeholder="Dark Vador...">
        </form>
        <div v-if="searchResults.length && searchQuery" class="navbar-search-results">
          <ul class="dropdown">
            <li v-for="(result, index) in searchResults" :key="index">
              <NuxtLink :to="'/characters/' + result.slug" @click="selectCharacter(result)">
                {{ result.name }}
              </NuxtLink>
            </li>
          </ul>
        </div>

      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      searchResults: [],
      selectedCharacter: null,
    };
  },

  methods: {
    async searchCharacters() {
      const searchResponse = await fetch(`https://swapi.dev/api/people/?search=${this.searchQuery}`);
      const searchResults = await searchResponse.json();

      if (searchResults.count > 0) {
        this.searchResults = searchResults.results.filter((result) => {
          const nameStart = result.name.toLowerCase().slice(0, 3);
          const queryStart = this.searchQuery.toLowerCase().slice(0, 3);
          return nameStart === queryStart;
        }).map((result) => ({
          name: result.name,
          slug: result.name.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/(^-|-$)+/g, ''),
        }));
      } else {
        this.searchResults = [];
      }
    },

    selectCharacter(result) {
      this.selectedCharacter = result;
      this.searchResults = [];
    }
  },
}

</script>

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

.navbar-search-results {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 100%;
  width: 300px;
  top: 80px;
}

.navbar-search-results li {
  flex-basis: 33%;
  cursor: pointer;
}
.navbar-search-results li a:hover{
  color: #d6b73c;
  border-bottom: 3px solid rgb(255, 255, 255);

}
.navbar-search{
  order: 2;
  position: relative;
}
.navbar-search input {
  background-color: black;
  border: 2px solid rgb(231, 181, 41);
  border-radius: 10px;
  padding: 4px;
  width: 300px;
  transition: all 0.1s ease-out;
  color: white;
  font-family: 'Lab Sans Pro', sans-serif;
  font-size: 20px;
  font-weight: bold;
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
    margin-top: 70px;
  }
  .navbar-search {
    margin-top: 20px;
    margin-bottom: 20px;
    order: 1;
  }

  .navbar-search-results {
    justify-content: center;
  }

  .dropdown{
    padding: 0;
  }
}

</style>