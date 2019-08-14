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
  name: 'Spotify',
  components: {
    TitleScreen,
    NewsStub,
    SlideControls,
    SummaryPane,
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
          week: 25,
          company: 'Tre',
          companyLogoUrl: 'tre.png',
          bgColor: '#ed9600',
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'barack-obama.jpg',
          source: {
            label: 'Dagens industri',
            url: 'https://www.di.se/nyheter/spotify-tecknar-avtal-med-paret-obama/'
          },
          title: 'Presidentiellt Podcast sammarbete',
          date: 'Måndagen den 10:e Juni',
          body: '<p>Michelle och Barack Obamas produktionsbolag <b>"Higher Ground"</b> sluter flerårigt avtal med Spotify, där Higher Ground ämnar skapa podcasts exklusivt för Spotifys plattformar.</p><br><p>Nyheterna om avtalet bemöttes positivt och gjorde att Spotifys aktiekurs lyfte med <b>3,4 %</b> samma dag.</p>'
        },
        {
          theme: 'dark',
          componentType: 'SummaryPane',
          trends: [
            'Mycket tyder på upptrappning av företagets satsningar på podcast marknaden.'
          ],
          challenges: [
            'Behöver motarbeta Apples framfart i USA när det kommer till musikmarknaden.',
            'Behöver etablera sig bättre på internationella marknader där inhemska alternativ idag regerar.'
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
