<template lang="html">
  <div class="company-container">
    <div id="news-section">
      <component
        v-for="(pane, index) in panes"
        :key="index"
        :is="pane.componentType"
        v-bind="pane"
      ></component>
    </div>
    <div class="pane-indicator">
      <SlideControls
        :activeItem="slides.activeSlide"
        :totalItem="panes.length"
        :theme="panes[slides.activeSlide - 1].theme"
        @on-update="setActiveSlide"
      ></SlideControls>
    </div>
  </div>
</template>

<script>
import TitleScreen from '~/components/TitleScreen.vue';
import NewsStub from '~/components/NewsStub.vue';
import SlideControls from '~/components/SlideControls.vue';
import SummaryPane from '~/components/SummaryPane.vue';

export default {
  name: 'Ica',
  components: {
    TitleScreen,
    NewsStub,
    SlideControls,
    SummaryPane
  },
  data(){
    return {
      slides: {
        activeSlide: 1,
      },
      panes: [
        {
          theme: 'dark',
          componentType: 'TitleScreen',
          company: 'ICA',
          companyLogoUrl: 'ica-logo-black-and-white.png',
          week: 24,
          bgColor: '#eb1e06'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'ica_spara.jpg',
          source: {
            label: 'Market',
            url: 'https://www.market.se/nyhet/ica-iskallt-i-maj-forsaljningen-rasade-for-supermarket-och-nara'
          },
          title: 'ICA inleder samarbete med Tink',
          date: 'Tisdagen den 11:e Juni',
          text: '<p>Appen <b>Ica Spara</b> integrerar <b>Tink</b> för att ge användarna en bättre överblick på deras konton och transaktioner. Upp till <b>25 olika banker och kort</b> kommer gå att visa i appen, vilket är <b>dubbelt</b> av vad som gått tidigare.</p>'
        },
        {
          theme: 'dark',
          componentType: 'SummaryPane',
          trends: [
            'Inga trender har kunnats identifieras denna vecka.',
          ],
          challenges: [
            'Inga utmaningar har identifierats denna vecka.',
          ],
        }
      ],
    }
  },
  methods: {
    setActiveSlide(action){
      if (action == 'next'){
        this.slides.activeSlide++
      } else {
        this.slides.activeSlide--
      }
    }
  },
  computed:{}
}
</script>

<style lang="css" scoped>

.company-container{
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

#news-section{
  position: relative;
  transition: 1s transform;

}

.pane-indicator{
  position: absolute;
  bottom: 150px;
  right: 100px;
}

</style>
