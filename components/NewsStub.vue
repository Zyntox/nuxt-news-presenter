<!--
  This is the news stub component, used for listing one single news pane in the
  presentation.

  Props:
  @imageUrl: string - as the name implies, the url to the image that will be displayed
                      to the left of the article body.
  @title: string    - The title of the news article.
  @source: string   - The soruce/ where the news article comes from.
  @date: string     - The date when the news article was written.
  @body: string     - The body of the news article,
-->

<template lang="html">
  <div class="news-stub">
    <div
      class="image-pane"
      :style="{ backgroundImage: `url( ${ require('@/assets/' + imageUrl ) } )` }"
    ></div>
    <div class="news-pane">
      <div class="inner-news-pane">
        <div class="article-header">
          <h1>{{ title }}</h1>
          <div class="sub-info">
            <div>{{ date }}</div>
            <div v-if="source">-
              <a :href="source.url">{{ source.label }}</a>
            </div>
          </div>
        </div>
        <div class="main-text" v-html="body"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewsStub',
  props: ['imageUrl', 'title', 'source', 'date', 'body'],
}
</script>

<style lang="scss" scoped>

  .news-stub{
    text-align: left;
    display: flex;

    .image-pane{
      display: inline-flex;
      background-color: lime;
      width: 39vw;
      height: 100vh;
      background-position: center center;
      background-size: cover;
    }

    .news-pane{
      width: 60vw;
      height: 100vh;
      display: inline-flex;
      justify-content: center;
      align-items: center;
      .inner-news-pane{
        text-align: left;
        min-width: 300px;
        max-width: 600px;

        .article-header{
          border-bottom: 1px solid #c1c1c1;
          padding-bottom: 30px;
          h1{
            font-size: 40px;
          }
        }

        .sub-info{
          div{
            display: inline-block;
            margin: 0px 10px 0px 0px;
          }
        }

        .main-text{
          font-size: 25px;
          line-height: 45px;
        }

      }
    }
  }
</style>
