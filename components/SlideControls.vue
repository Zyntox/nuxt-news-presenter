<template lang="html">
  <div class="slide-controls">
    <div
      class="arrow"
      v-show="activeItem > 1"
      @click="slideToPreviousPane()"
    ><</div>
    <div class="numbering">
      <span>{{ activeItem }}</span>
      <span class="divider"> / </span>
      <span>{{ totalItem }}</span>
    </div>
    <span
      class="arrow"
      v-show="activeItem < totalItem"
      @click="slideToNextPane()"
    >></span>
  </div>
</template>

<script>
export default {
  name: 'SlideControls',
  props: ['totalItem'],
  data(){
    return {
      activeItem: 1,
    }
  },
  methods: {
    slideToNextPane(){
      let slidesList = document.getElementById('news-section');
      let slides = document.getElementById('news-section').childNodes;

      slidesList.style.transform = `translateY(-${slides[0].offsetHeight * this.activeItem}px)`
      this.activeItem++;
    },
    slideToPreviousPane(){
      let slidesList = document.getElementById('news-section');
      let slides = document.getElementById('news-section').childNodes;

      slidesList.style.transform = `translateY(-${slides[0].offsetHeight * (this.activeItem - 2)}px)`
      this.activeItem--;
    }
  },
}
</script>

<style lang="scss" scoped>

.slide-controls{
  width: 100px;
  height: 100px;
  font-size: 45px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-weight: 100;

  .numbering{
    width: 150px;
  }

  .divider{
    margin: 0px 10px;
  }


  .arrow{
    display: block;
    transform: rotate(90deg);
    z-index: 999;
    cursor: pointer;
    display: inline-block;
    margin: 0px 15px;

    &:hover{
      opacity: 1;
      color: #95b7f1;
    }

  }

}


</style>
