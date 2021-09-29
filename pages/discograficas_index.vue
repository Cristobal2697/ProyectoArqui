<script>
  export default {
    async asyncData({ $content, params }) {
      const discograficas = await $content('discograficas').fetch()
      return {
        discograficas
      }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <h3 style="margin-top: 15px">Discograficas Information</h3>
     <p>This section presents information about discograficas</p>
   <ul>
     <li v-for="d of discograficas" :key="d.slug">
       <NuxtLink :to="{ name: 'discograficas-slug', params: { slug: d.slug } }">{{d.name}}</NuxtLink>
     </li>
   </ul>
   <FooterView />
 </div>
</template>