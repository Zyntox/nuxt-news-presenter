<template>
  <div class="container">
    <div>
      <h2 class="subtitle">
        Företag
      </h2>
      <nuxt-link to="/companies/ica">ICA</nuxt-link>
      <nuxt-link to="/companies/spotify">Spotify</nuxt-link>
    </div>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'

export default {
  components: {},
  transition: 'page',
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
