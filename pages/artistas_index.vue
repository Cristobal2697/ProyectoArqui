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
   <h3 style="margin-top: 15px">Artistas Information</h3>
     <p>This section presents information about artistas</p>
   <ul>
     <li v-for="a of artistas" :key="a.slug">
       <NuxtLink :to="{ name: 'artistas-slug', params: { slug: a.slug } }">{{a.name}}</NuxtLink>
     </li>
   </ul>
   <FooterView />
 </div>
</template>