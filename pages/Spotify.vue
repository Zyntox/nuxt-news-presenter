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
          week: 24,
          company: 'Spotify',
          companyLogoUrl: 'Spotify_Logo_RGB_White.png',
          bgColor: '#24cf5f',
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
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'stations.jpg',
          source: {
            label: 'Market Realist',
            url: 'https://marketrealist.com/2019/06/spotify-introduces-a-new-us-product-amid-growing-apple-threat/'
          },
          title: 'Lansering av ny app: "Stations" i USA ',
          date: 'Måndagen den 10:e Juni',
          body: '<p>Spotify lanserar appen <b>"Stations"</b> i USA, en separat app från den primära, vilket ger användaren möjligheten att skapa radio-liknande stationer från spellistor eller användarens favoritartister.</p><br> <p>Appen har tidigare lanserats i Australien och beslutet att lansera den nu även I USA kan vara ett sätt för Spotify att tackla Apples framfart.</p>'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'sound-up.jpeg',
          source: {
            label: 'Music ally',
            url: 'https://musically.com/2019/06/10/spotify-repeats-sound-up-podcasts-program-for-women-of-colour/'
          },
          title: 'Spotify lyfter fram minoriteter för att skapa podcasts',
          date: 'Måndagen den 6:e Juni',
          body: 'Spotify gör comeback med <b>"Sound Up"</b>, en femdagars podcast-accelerator program för färgade kvinnor. Programmet tar plats I New York under sommaren och ämnar lyfta fram personer med bakgrunder som inte är framträdande inom podcast sfären.'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'spotify-redesign.png',
          source: {
            label: 'Tech Crunch',
            url: 'https://techcrunch.com/2019/06/13/spotifys-redesign-simplifies-navigation-and-highlights-podcasts/',
          },
          title: 'Spotify rullar ut en ny design för sina appar',
          date: 'Torsdagen den 13:e Juni',
          body: '<p>Företaget annonserade under dagen ut planenrna att lansera en ny design av sina appar. Den nya designen gör det möjlight för premium användare att kunna enklare välja mellan musik eller podcasts, genom sektionen <b>"Your Library"</b>. Designen skapar även tre nya sektioner för podcasthantering: <b>"Episodes", "Downloads" och "Shows".<b/> <p>'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'news',
          imageUrl: 'playstation.jpg',
          source: {
            label: 'Tech Radar',
            url: 'https://www.techradar.com/news/spotify-now-available-on-playstation-music-across-uae-saudi-arabia-and-more',
          },
          title: 'Spotify lanseras på Playstation Music i mellanöstern ',
          date: 'Tisdagen den 11:e Juni',
          body: '<p>Gamers i länderna Saudi Arabien, Förenade arab emiraten, Kuwait, Qatar, Bahrain, Oman och Libanon får nu möjligheten att streama musik via spotifys tjänster, när de spelar på antingen playstation 3 eller 4.</p><br/><p>Med detta så har Spotify uppfyllt det löfte som de gav för <b>fyra år sedan</b> när de lovade att deras tjänter skulle finnas tillgängliga på Playstation Music.</p>'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'challenge',
          imageUrl: 'india.jpg',
          source: {
            label: 'Live Mint',
            url: 'https://www.livemint.com/technology/apps/india-is-going-global-on-spotify-1560238704744.html',
          },
          title: 'Spotifys närvaro I indien sedan releasen... ',
          date: 'Tidagen den 11:e Juni',
          body: '<p>Sedan lanseringen av Spotify i Indien i början av Februari, så har <b>2 miljoner</b> indiska användare registrerat sig på plattformen.</p><br><p>Varje månad så registreras det <b>11 miljoner gånger</b> att användare lyssnat på en ny artist, vilket visar på en trend att användarbasen är öppen för nya musikupplevelser.</p><br/><p>De största konkurrenterna till spotify i Indien är för nuvarande de inhemska apparna <b>"Gaana"</b> och <b>"JioSaavn"</b>, där den förstnämnda sägs av ägarna Times Internet, ha <b>80 miljoner användare per månad</b>.</p>'
        },
        {
          theme: 'light',
          componentType: 'NewsStub',
          category: 'challenge',
          imageUrl: 'apple.jpg',
          source: {
            label: 'Market Realist',
            url: 'https://marketrealist.com/2019/06/spotify-introduces-a-new-us-product-amid-growing-apple-threat/'
          },
          date: 'Tisdagen Den 11:e Juni',
          title: 'Spotify halkar efter Apple i antalet betalande användare i USA',
          body: '<p>Wall street journal rapporterade tidigare i April att Apple gått om Spotify när det kommer till antalet betalande användare på den amerikanska marknaden. Trots detta så leder Spotify fortfarande när det kommer till det totala antalet användare, både i USA och internationellt.</p> <br/> <p>I februari så hade Spotify <b>26 miljoner betalande användare</b> på den amerikanska marknaden och  vid samma tillfälle så hade Apple <b>28 miljoner betalande användare</b> på den amerikanska marknaden.</p>'
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
