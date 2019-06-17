<template lang="html">
  <div class="company-container">
    <TitleScreen
      company="Ica"
      :week="24"
      bgColor="#eb1e06"
    ></TitleScreen>
    <div id="news-section">
      <NewsStub
        v-for="(article, index) in articles"
        :key="index"
        :imageUrl="article.imageUrl"
        :title="article.title"
        :source="article.source"
        :date="article.date"
        :text="article.text"
      ></NewsStub>
      <div class="test-pane">
      </div>
    </div>
    <div class="pane-indicator">
      <SlideControls
        :activeItem="slides.currentSlide"
        :totalItem="articles.length"
      ></SlideControls>
    </div>
  </div>
</template>

<script>
import TitleScreen from '~/components/TitleScreen.vue';
import NewsStub from '~/components/NewsStub.vue';
import SlideControls from '~/components/SlideControls.vue';

export default {
  name: 'Ica',
  components: {
    TitleScreen,
    NewsStub,
    SlideControls
  },
  data(){
    return {
      slides: {
        currentSlide: 1,
      },
      articles: [
        {
          category: 'news',
          imageUrl: 'barack-obama.jpg',
          source: {
            label: 'Dagens industri',
            url: 'https://www.di.se/nyheter/spotify-tecknar-avtal-med-paret-obama/'
          },
          title: 'Presidentiellt Podcast sammarbete',
          date: 'Måndagen den 10:e Juni',
          text: '<p>Michelle och Barack Obamas produktionsbolag <b>"Higher Ground"</b> sluter flerårigt avtal med Spotify, där Higher Ground ämnar skapa podcasts exklusivt för Spotifys plattformar.</p><p>Nyheterna om avtalet bemöttes positivt och gjorde att Spotifys aktiekurs lyfte med <b>3,4 %</b> samma dag.</p>'
        },
      ],
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
  background-color: #f4f4f4;
}

.pane-indicator{
  position: absolute;
  bottom: 150px;
  right: 100px;
}

</style>
