<template lang="html">
  <div class="title-screen" :style="{ backgroundColor: bgColor }">
    <div class="rectangle-container">
      <h1>{{ company }} Nyheter</h1>
      <h4>Vecka {{ week }}</h4>
    </div>
    <!-- <img src="../assets/Spotify_Logo_RGB_White.eps" alt=""> -->
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

  .title-screen{;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    background-color: lime;


    .rectangle-container{
      width: 100vw;
      height: 100vh;
      // background-image: linear-gradient(to right top, #b5eb45, #a8e53c, #9adf34, #8cd92b, #7ed321);
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      color: #fff;

      h1{
        font-size: 80px;
      }
      h4{
        font-size: 30px;
      }

    }
  }

</style>
