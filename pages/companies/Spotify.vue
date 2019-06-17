<template lang="html">
  <div class="company-container">
    <TitleScreen
      company="Spotify"
      :week="24"
      bgColor="#24cf5f"
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
  name: 'Spotify',
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
        {
          category: 'news',
          imageUrl: 'stations.jpg',
          source: {
            label: 'Market Realist',
            url: 'https://marketrealist.com/2019/06/spotify-introduces-a-new-us-product-amid-growing-apple-threat/'
          },
          title: 'Lansering av ny app: "Stations" i USA ',
          date: 'Måndagen den 10:e Juni',
          text: '<p>Spotify lanserar appen "stations" i USA, en separat app från den primära, vilket ger användaren möjligheten att skapa radio-liknande stationer från spellistor eller användarens favorit artister.</p> <p>Appen har tidigare lanserats i Australien och beslutet att lansera den nu även I USA kan vara en indikator på appens tidigare framgång.</p>'
        },
        {
          category: 'news',
          imageUrl: 'sound-up.jpeg',
          source: {
            label: 'Music ally',
            url: 'https://musically.com/2019/06/10/spotify-repeats-sound-up-podcasts-program-for-women-of-colour/'
          },
          title: 'Spotify lyfter fram minoriteter för att skapa podcasts',
          date: 'Måndagen den 6:e Juni',
          text: 'Spotify gör comeback med deras "Sound Up", en femdagars podcast-accelerator program för färgade kvinnor. Programmet tar plats I New York under sommaren och ämnar lyfta fram personer med bakgrunder som inte är framträdande inom podcast sfären.'
        },
        {
          category: 'news',
          imageUrl: 'playstation.jpg',
          source: {
            label: 'Tech Radar',
            url: 'https://www.techradar.com/news/spotify-now-available-on-playstation-music-across-uae-saudi-arabia-and-more',
          },
          title: 'Spotify lanseras på Playstation Music i mellanöstern ',
          date: 'Tisdagen den 11:e Juni',
          text: '<p>Gamers i länderna Saudi Arabien, Förenade arab emiraten, Kuwait, Qatar, Bahrain, Oman och Libanon får nu möjligheten att streama musik via spotifys tjänster, när de spelar på antingen playstation 3 eller 4.</p> <p>Med detta så har Spotify uppfyllt det löfte som de gav för fyra år sedan när de lovade att deras tjänter skulle finnas tillgängliga på Playstation Music.</p>'
        },
        {
          category: 'challenge',
          imageUrl: 'india.jpg',
          source: {
            label: 'Live Mint',
            url: 'https://www.livemint.com/technology/apps/india-is-going-global-on-spotify-1560238704744.html',
          },
          title: 'Spotifys närvaro I indien sedan releasen... ',
          date: 'Tidagen den 11:e Juni',
          text: '<p>Sedan lanseringen av Spotify i Indien i början av Februari, så har 2 miljoner indiska användare registrerat sig på plattformen.  Varje månad så registreras det 11 miljoner gånger att användare lyssnat på en ny artist, vilket visar på en trend att användarbasen är öppen för nya musikupplevelser.</p> <p>De största konkurrenterna till spotify i Indien är för nuvarande de inhemska apparna <b>"Gaana"</b> och <b>"JioSaavn"</b>, där den förstnämnda sägs av ägarna Times Internet, ha 80 miljoner användare per månad.</p>'
        },
        {
          category: 'challenge',
          imageUrl: 'webben-anna.jpg',
          title: 'Kommunikationsproblem och bemanningsöverflöd?',
          date: 'Torsdagen den 7:e Juni',
          text: 'Grundaren av företaget Artifical Humanity, Anna Loverus berättar om hur hon använde sig av AI för att automatisera sitt jobb som "social mediechef" under de 10 månader som hon arbetade på Spotify. I artikeln framgår hur tilltaget inte gjorde henne särskillt poupulär bland kollegorna som nu börjat oroa sig för att förlora sina egna arbeten.<br><br><i>”Jag satt egentligen bara mellan folk i olika processer. Tittar du på organisationer mer strukturerat och utifrån ett helhetsperspektiv så inser du snart att det går att scripta bort en massa människor.”</i>'
        },
        {
          category: 'challenge',
          imageUrl: 'apple.jpg',
          source: {
            label: 'Market Realist',
            url: 'https://marketrealist.com/2019/06/spotify-introduces-a-new-us-product-amid-growing-apple-threat/'
          },
          date: 'Tisdagen Den 11:e Juni',
          title: 'Spotify halkar efter Apple i antalet betalande användare i USA',
          text: '<p>Wall street journal rapporterade tidigare i April att Apple gått om Spotify  när det kommer till antalet betalande användare på den amerikanska marknaden. Trots detta så leder Spotify fortfarande när det kommer till det totala antalet användare, både i USA och internationellt.</p><p>I februari så hade Spotify 26 miljoner betalande användare på den amerikanska marknaden och  vid samma tillfälle så hade Apple 28 miljoner betalande användare på den amerikanska marknaden.</p>'
        }
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
