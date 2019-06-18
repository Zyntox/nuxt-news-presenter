<template lang="html">
  <div class="title-screen" :style="{ backgroundColor: bgColor }">
    <nuxt-link to="/" class="back-navigation">Tillbaka</nuxt-link>
    <div class="rectangle-container">
      <div
        v-if="companyLogoUrl"
        class="company-logo-container"
        :style="{ backgroundImage: `url( ${ require('@/assets/' + companyLogoUrl ) } )` }"
      ></div>
      <h1>Nyheter</h1>
      <h4>Vecka: {{ week }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TitleScreen',
  props: {
    company: {
      type: String,
      default() { return 'placeholder' }
    },
    companyLogoUrl: {
      type: String,
      default() { return null }
    },
    week: {
      type: Number,
      default() { return 0 },
    },
    bgColor: {
      type: String,
      default() { return '#4f4f4f' },
    }
  }
}
</script>

<style lang="scss" scoped>

  .title-screen{
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    background-color: lime;

    .back-navigation{
      position: absolute;
      left: 50px;
      top:50px;
      border: 1px solid #fff;
      border-radius: 5px;
      padding: 10px;
      color: #fff;
      font-weight: 200;
      opacity: 0.5;
      transition: 0.5s opacity;
      text-decoration: none;

      &:hover{
        opacity: 1;
      }

    }

    .rectangle-container{
      width: 100vw;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      color: #fff;

      .company-logo-container{
        width: 200px;
        height:150px;
        background-size: contain;
        background-position: bottom;
        background-repeat: no-repeat;
      }

      h1{
        font-size: 80px;
        margin: 15px 0px;
      }
      h4{
        margin: 30px 0px;
        font-size: 30px;
        font-weight: 300;
      }

    }
  }

</style>
