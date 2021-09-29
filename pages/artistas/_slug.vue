<script>
  export default {
    async asyncData({ $content, params }) {
      const artista = await $content('artistas', params.slug).fetch()
      const album = await $content('album').where({ artistaId: params.slug }).fetch()
      return { artista, album }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="'/images/'+artista.image" alt="Italian Trulli">
     </div>
     <div class="six columns">
       <h4>{{artista.name}}</h4>
	   Nationality: {{artista.nationality}}; Born: {{artista.birth_year}}<br>
	   Fields: {{artista.fields}}<br><br>
	   <b>Biography</b><br>
	    <nuxt-content :document="artista" />
	 </div>
	 <div class="three columns"></div>
	   <h5>Álbumes</h5>
	   <ul>
	     <li v-for="a of album" :key="a.slug">
	       <NuxtLink :to="{ name: 'album-slug', params: { slug: a.slug } }">{{a.title}}</NuxtLink>
	     </li>
	   </ul>
   </div>
   <FooterView />
 </div>
</template>