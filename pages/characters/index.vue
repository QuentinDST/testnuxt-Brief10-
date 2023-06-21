<template>
    <main>
        <div class="container">
            <div class="row text-center mt-5 justify-content-center listing--page">
                <div class="col-12 mt-5 mb-5">
                    <H1>CHARACTERS STAR WARS  !</H1>
                </div>
                <div class="col-12 mb-5 d-flex justify-content-center">
                  <Btn class="btn-listing" url="/contact" text="FILTERR BY CATEGORY" />
                </div>
            </div>

            <div class="row mt-5">
                <div class="d-flex flex-wrap character-box">
                  <character v-for="character in characters" :key="character.name"  :character="character"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import Character from "@/components/Character.vue";

export default {
  data() {
    return {
      characters: [],
    };
  },
  async fetch() { //fetch pour récup tous les characters de l'API
    let url = "https://swapi.dev/api/people/";
    let allCharacters = []; // on stocke tout ca dans dans un tableau

    while (url) { // On boucle ensuite sur l'url
      const response = await fetch(url).then((res) => res.json());
      url = response.next;
      allCharacters = allCharacters.concat(response.results);
    }

    this.characters = allCharacters; // on injecte ensuite les données du tableau dans "characters"
  }
};
</script>

<style>

body{
  background: url('~assets/images/starwars.jpg');
}


H1{
  font-family: 'Poller One';
  color: white;
}

.btn-listing{
  width: 350px;
}


.character-box {
  display: flex;
  flex-wrap: wrap;
}

.character-box > * {
  flex: 0 0 calc(25% - 20px);
  margin-right: 20px;
  margin-bottom: 20px;
}

@media screen and (max-width: 768px) {
  .character-box > * {
    flex: 0 0 calc(50% - 20px);
  }
}

</style>