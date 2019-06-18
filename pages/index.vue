<template>
  <div class="container">
    <div>
      <h2 class="subtitle">
        Välj Företag
      </h2>
      <nuxt-link to="/ica">ICA</nuxt-link>
      <nuxt-link to="/spotify">Spotify</nuxt-link>
    </div>
  </div>
</template>

<script>
import CompanySelector from '~/components/CompanySelector.vue';
export default {
  components: {
    CompanySelector,
  },
  transition: 'page',
}
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

  a{
    color: #696969;
    display: inline-block;
    font-size: 25px;
    margin: 50px 20px;
    text-decoration: none;
    transition: 0.5s color;

    &:hover{
      color: #856093;
    }

  }


}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

</style>
