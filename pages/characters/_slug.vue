<template>
    <body class="no-footer-shadow">
        <div v-if="character" class="container">
            <div class="row d-flex justify-content-center mt-5">
                <div class="col-12 mt-5 text-center">
                    <h1>{{ character.name }}</h1>
                </div>
            </div>

            <div class="row mt-5 mb-5">
                <div class="col-sm-12 col-md-12 col-lg-4 identity">
                    <div class="identity--title">
                        <H2>IDENTITE</H2>
                    </div>
                   <div class="identity--content">
                        <p class="identity--content--p">Gender : {{ character.gender }}</p>
                        <p class="identity--content--p">Height : {{ character.height }} cm</p>
                        <p class="identity--content--p">Mass : {{ character.mass }} kg</p>
                        <p class="identity--content--p">Skin Color : {{ character.skin_color }}</p>
                        <p class="identity--content--p">Birth Year : {{ character.birth_year }}</p>
                    </div>
                </div>
                <div class="col-sm-12 col-md-12 col-lg-4 p-5 justify-content-center image">
                  <img :src="characterImageUrl" alt="personnage">
                </div>
                <div class="col-sm-12 col-md-12 col-lg-4  films">
                    <div class="text-right">
                        <h2>FILMS</h2>
                    </div>
                    <div class="film--content">
                        <div class="film--item"><img src="~/assets/images/couverture1.jpg"></div>
                        <div class="film--item"><img src="~/assets/images/couverture2.jpg"></div>
                        <div class="film--item"><img src="~/assets/images/couverture3.jpg"></div>
                        <div class="film--item"><img src="~/assets/images/couverture4.jpg"></div>
                    </div>
                </div>
            </div>
        </div>
    </body>
</template>

<script>
export default {
  data() {
    return {
      character: {},
      characterImageUrl: null
    }
  },

  async fetch() {
    const slug = this.$route.params.slug;
    const name = slug.replace(/-/g, ' '); // Remplace les tirets par des espaces
    
    const characterData = await fetch(`https://swapi.dev/api/people/?search=${name}`).then(res => res.json())

    if (characterData.count > 0) {
      this.character = characterData.results[0];
      this.character.name = this.character.name.replace(/-/g, ' ');
      this.characterImageUrl = `https://starwars-visualguide.com/assets/img/characters/${this.getCharacterId()}.jpg`;
    } else {
      console.log('Aucun personnage trouvé pour cette recherche');
    }
  },

  methods: {
    getCharacterId() {
      // Extrait l'ID du personnage à partir de l'URL de l'API
      const characterUrlParts = this.character.url.split('/');
      return characterUrlParts[characterUrlParts.length - 2];
    }
  },
}

</script>

<style scoped>

.container{
    margin-bottom: 100px;
}

H1, H2{
  font-family: 'Poller One';
  color: white;
}


.identity{
  /*   border-left: 1px solid #d6b73c(211, 131, 10, 0.5);
    border-bottom: 1px solid #d6b73c(211, 131, 10, 0.5);  */
    box-shadow: -5px 5px 5px 0px rgba(244, 169, 58, 0.79);
    height: 450px;
    width: 350px;
    padding-left: 20px;
}

.identity--title{
    margin-bottom: 40px;
}

.identity--content{
    display: flex;
    flex-direction: column;
    height: 100%;
}

.identity--content--p{
    margin-bottom: 25px;
    font-family: 'Lab Sans Pro', sans-serif;
    font-size: 28px;
    font-weight: bold;
    color: white;
}

.image{
    height: 450px;
    width: 350px;
    padding-left: 20px;
}
.image img{
    max-width: 100%; 
    max-height: 100%; 
    object-fit: cover;
    border-radius: 5px;
}
.image img:hover{
    box-shadow: 0px 0px 2px #fff, 0px 0px 4px #fff, 0px 0px 6px #fff, 0px 0px 8px #a4a39d, 0px 0px 10px #b9b7a9, 0px 0px 12px #eecb41, 0px 0px 16px #e6bc17, 0px 0px 20px #fff;
}

.films{/* 
    border-right: 1px solid rgb(212, 205, 205); 
    border-bottom: 1px solid rgb(212, 205, 205);  */
    box-shadow: 5px 5px 5px 0px rgb(123, 119, 119);
    height: 450px;
}

.film--content {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
}

.film--item {
  padding: 10px;
  width: 120px;
  height: 170px;
}
.film--item:hover {
  cursor: pointer;
}

.film--item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.film--item img:hover {
    box-shadow: 5px 5px 5px 0px rgb(123, 119, 119);
    cursor: pointer;
}

@media screen and (max-width: 580px) {
  .identity{
    margin-left: 40px;
  }
  .films{
    margin-right: 40px;
  }

  .image{
    align-items: center;
  }
}

@media screen and (max-width: 992px) {
  .image{
    margin: auto;
  }
}

</style>