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
          company: 'Telenor',
          companyLogoUrl: 'Telenor.png',
          bgColor: '#03acfb',
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'norge-telenor.jpg',
          source: {
            label: 'Global Competions review',
            url: 'https://globalcompetitionreview.com/article/1194418/norway-upholds-record-fine-on-telenor'
          },
          title: 'Telenor får betala rekodhöga böter i Norge',
          date: 'Måndagen den 24:e Juni',
          body: '<p>I en två-mot-en-röstning så dömde Norges konkurrensverk under måndagen, Telenor till att betala 788 miljoner NOK i böter. Beslutet grundas i hur de ansett Telenor missbrukat sin marknadsledande position i landet under åren 2010 till 2014.</p><br /><p>Telenor har nu tre månader på sig att överklaga beslutet. </p>  </landet></p>'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'norge-telenor.jpg',
          source: {
            label: 'Global Competions review',
            url: 'https://globalcompetitionreview.com/article/1194418/norway-upholds-record-fine-on-telenor'
          },
          title: 'Telenor får betala rekodhöga böter i Norge',
          date: 'Måndagen den 24:e Juni',
          body: '<p>I en två-mot-en-röstning så dömde Norges konkurrensverk under måndagen, Telenor till att betala 788 miljoner NOK i böter. Beslutet grundas i hur de ansett Telenor missbrukat sin marknadsledande position i landet under åren 2010 till 2014.</p><br /><p>Telenor har nu tre månader på sig att överklaga beslutet. </p>  </landet></p>'
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
