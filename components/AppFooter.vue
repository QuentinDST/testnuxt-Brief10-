<script>
</script>

<template>
    <footer class="no-shadow">
        <div class="container">
            <div class="row h-100 footer--content text-center">
                <div class="col-md-4 footer--items">
                    <NuxtLink to="/mentionslegales">
                        Mentions Légales
                    </NuxtLink>
                </div>
                <div class="col-md-4 footer--items">
                    <NuxtLink to="/contact">
                        Contact
                    </NuxtLink>
                </div>
                <div class="col-md-4 mx-auto">
                    <NuxtLink to="/reseau">
                        Réseau
                    </NuxtLink>
                </div>
            </div>
        </div>
    </footer>
</template>

<style scoped> /* Scoped = applique du style uniquement sur le fichier sur lequel on est en train de travailler */

@import url('https://fonts.cdnfonts.com/css/lab-sans-pro');

.row {
  height: 100%;
}


footer {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
}

.footer--items{
    border-right: 2px solid #fff;
    box-shadow: 0px 2px rgba(238, 222, 222, 0.714) 4px rgba(228, 203, 10, 0.652);
}

a{
    font-family: 'Lab Sans Pro', sans-serif;
    font-size: 25px;
    font-weight: bold;
    letter-spacing: 0.4px;
    color: white;
    text-decoration: none;
    transition: all 0.1s ease-out;
    
}

a:hover {
    border-bottom: 3px solid rgb(231, 181, 41);
    padding-bottom: 3px;
}

@media screen and (max-width: 600px) {
    a{
    margin-bottom: 15px;
}
}

@media screen and (max-width: 770px) {
    .footer--items{
        border-right: none;
   box-shadow: none;
}
}

</style>