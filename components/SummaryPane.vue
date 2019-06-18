<template lang="html">
  <div class="summary-pane">
    <nuxt-link to="/" class="back-navigation">Tillbaka</nuxt-link>
    <div>
      <div class="list-section">
        <h2>Pågående trender</h2>
        <ul>
          <li
            v-for="(trend, index) in trends"
            :key="index"
          >{{ trend }}</li>
        </ul>
      </div>

      <div class="list-section">
        <h2>Utmaningar</h2>
        <ul>
          <li
            v-for="(challenge, index) in challenges"
            :key="index"
          >{{ challenge }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SummaryPane',
  props: {
    trends: {
      type: Array,
      default() { return null },
    },
    challenges: {
      type: Array,
      default() { return null }
    }
  }
}
</script>

<style lang="scss" scoped>

  .summary-pane{
    position: relative;
    width: 100vw;
    height: calc(100vh + 5px);
    background-color: #2a2a2a;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: #fff;
  }

  .list-section{
    margin: 50px 0px;
  }

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


  h2{
    color:#fff;
    border-bottom: 1px solid #fff;
    padding: 20px 0px;
    font-weight: 200;
    font-size: 40px;
  }

  ul{
    margin: 0;
    li{
      padding: 20px 0px;
      font-size: 25px;
      font-weight: 300;
      color: #bfbfbf;
    }
  }

</style>
