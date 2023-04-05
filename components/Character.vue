<template>
    <div class="personnage mx-auto mb-5">
        <div class="image" :style="{ backgroundImage: `url(${characterImageUrl})` }">
        </div>
        <div class="name">
            <NuxtLink :to="url">{{character.name}}</NuxtLink>
        </div>
    </div>
</template>

<script>
 import slugify from 'slugify' 

export default {
    data() {
        return {
            url: `/characters/${slugify(this.character.name, { lower: true })}`
        }
    },

    props: {
        character: {
            type: Object,
            required: true
        },
    },  

    computed: {
       slug() {
         return slugify(this.character.name, { lower: true })
        },
        characterImageUrl() {
            return `https://starwars-visualguide.com/assets/img/characters/${this.getCharacterId()}.jpg`;
        }
    }, 

    methods: {
        getCharacterId() {
            // Extrait l'ID du personnage à partir de l'URL de l'API
            const characterUrlParts = this.character.url.split('/');
            return characterUrlParts[characterUrlParts.length - 2];
        }
    },

    mounted() {
        console.log(this.character.name);
     }
};
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poller+One&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

.personnage {
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;
    padding: 20px;
    max-width: 300px;
}
.personnage {
    cursor: pointer;
}

.image {
    background-position: center center;
    background-size: cover;
    width: 200px;
    height: 200px;
    border-radius: 100%;
    overflow: hidden;
    margin-bottom: 20px;
    box-shadow: 0px 0px 4px #fff, 0px 0px 8px #fff, 0px 0px 10px #fff, 0px 0px 12px #ffdd00, 0px 0px 15px #ffdd00, 0px 0px 20px #e7b811, 0px 0px 25px #e7b811, 0px 0px 30px #fff;
}
.image:hover {
    box-shadow: 0px 0px 2px #fff, 0px 0px 4px #fff, 0px 0px 6px #fff, 0px 0px 8px #ffdd00, 0px 0px 10px #ffdd00, 0px 0px 12px #ffdd00, 0px 0px 16px #ffdd00, 0px 0px 20px #fff;
}

.image img {
    width: 100%;
    height: 100%;
    
}

.name{
    margin-top: 35px;
}

a{
    font-size: 30px;
    font-family: 'Lab Sans Pro', sans-serif;
    font-weight: bold;
    text-align: center;
    color: white;
    margin-top: 30px;
    margin: 0;
}

a:hover {
    border-bottom: 3px solid rgb(231, 181, 41);
    padding-bottom: 3px;
    text-decoration: none;
}
</style>