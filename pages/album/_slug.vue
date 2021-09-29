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
	   by <NuxtLink :to="'/artistas/'+album.artistaId">{{album.artista}}</NuxtLink><br>
	   Edition: {{album.edition}}; Copyright: {{album.copyright}}; 
	   Language: {{album.language}}; Pages: {{album.pages}}<br>
	   published by <NuxtLink :to="'/discograficas/'+album.discograficaId">{{album.discografica}}</NuxtLink><br><br>
	   <b>Description</b><br>
	    <nuxt-content :document="album" />
	 </div>
	 <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>