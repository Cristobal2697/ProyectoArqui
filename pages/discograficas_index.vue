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
     <ul class="ul">
          <li v-for="d of discograficas" :key="d.slug">
            <div class="card">
              <div>
                <img class="card-img" :src="'/images/' + d.image" />
              </div>
              <div class="card-text">
                <h4 class="card-title"><strong> {{ d.name }} </strong></h4>
                <p class="card-description">
                  <span>País: {{d.country}}</span><br>
                  <span>Fundadación: {{d.founded}}</span><br>
                  <span>Género: {{d.genere}}</span><br>
                </p>
                <NuxtLink :to="{ name: 'discograficas-slug', params: { slug: d.slug } }" class="button">
                    Detalles
                </NuxtLink>
              </div>
            </div>
          </li>
        </ul>
   <FooterView />
 </div>
</template>
