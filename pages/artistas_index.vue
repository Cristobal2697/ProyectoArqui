<script>
  export default {
    async asyncData({ $content, params }) {
      const artistas = await $content('artistas').fetch()
      return {
        artistas
      }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <h3 style="margin-top: 15px">Artistas </h3>
   <ul class="ul">
     <li v-for="a of artistas" :key="a.slug">
       <div class="card">
          <div>
            <img class="card-img" :src="'/images/' + a.image" />
          </div>
          <div class="card-text">
            <h4 class="card-title"><strong> {{ a.name }} </strong></h4>
            <p class="card-description">
              <span>Nacionalidad: {{a.nationality}}</span><br>
              <span>Nacimiento: {{a.birth_year}}</span><br>
            </p>
            <NuxtLink :to="{ name: 'artistas-slug', params: { slug: a.slug } }" class="button">
                Detalles
            </NuxtLink>
          </div>
        </div>
     </li>
   </ul>
   <FooterView />
 </div>
</template>