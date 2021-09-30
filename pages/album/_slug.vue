<script>
  export default {
    async asyncData({ $content, params }) {
      const album = await $content('album', params.slug).fetch()
        return { album }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="'/images/'+album.image" alt="Italian Trulli">
     </div>
     <div class="six columns">
       <h4>{{album.title}}</h4>
	   Artista: <NuxtLink :to="'/artistas/'+album.artistaId">{{album.artista}}</NuxtLink><br>
	   
	   Duración: {{album.duracion}}<br>
	   Año de publicación: {{album.copyright}} <br>
	   Publicado por <NuxtLink :to="'/discograficas/'+album.discograficaId">{{album.discografica}}</NuxtLink><br><br>
	   <b>Canciones: </b><br>
	    <nuxt-content :document="album" />
	 </div>
	 <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>