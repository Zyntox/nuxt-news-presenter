
<!--
  This is the Title Screen component, it is used to list the company name,
  company logotype and what week the proceeding news article are from.

  Params:
  @theme: string - Set if the theme is 'light' or 'dark'.
  @company: string - The company the news are about.
  @companyLogoUrl: string - The name of the company logo in assets folder.
  @week: number - The week the articles were written.
  @bgColor: string - a hexadecimal value for setting the panes background color.
-->

<template lang="html">
  <div :class="`title-screen`" :style="{ backgroundColor: bgColor }">
    <nuxt-link to="/" :class="`back-navigation ${ theme }-pane-theme`">Tillbaka</nuxt-link>
    <div :class="`rectangle-container ${ theme }-pane-theme`">
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
    theme:{
      type: String,
      default() { return 'light' }
    },
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

      &.light-pane-theme{
        color: #000 !important;
        border-color: #000;
      }

      &.dark-pane-theme{
        color: #fff !important;
        border-color: #fff;
      }

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

      &.light-pane-theme{
        color: #000 !important;
      }

      &.dark-pane-theme{
        color: #fff !important;
      }

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
