<!--
  This is the Slide controls component, it is used to act as a GUI element for
  the controls used to slide the presentation up or down.

  Params:
  @activeItem: number - The number representing the currently active slide.
  @totalItem: number - The total number of all the slides combined.
  @theme: string - String controlling if the displayed text of the component
                   should be light or dark.
-->

<template lang="html">
  <div :class="`slide-controls ${ theme }-pane-theme`">
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
  props: ['activeItem', 'totalItem', 'theme'],
  methods: {
    slideToNextPane(){
      let slidesList = document.getElementById('news-section');
      let slides = document.getElementById('news-section').childNodes;

      slidesList.style.transform = `translateY(-${slides[0].offsetHeight * this.activeItem}px)`
      // this.activeItem++;
      this.$emit('on-update', 'next');
    },
    slideToPreviousPane(){
      let slidesList = document.getElementById('news-section');
      let slides = document.getElementById('news-section').childNodes;

      slidesList.style.transform = `translateY(-${slides[0].offsetHeight * (this.activeItem - 2)}px)`
      // this.activeItem--;
      this.$emit('on-update', 'previous');
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
  transition: 1s color;

  &.light-pane-theme{
    color: #000;
  }

  &.dark-pane-theme{
    color: #fff;
  }

  .numbering{
    text-align: center;
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
