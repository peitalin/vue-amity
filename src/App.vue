
<template>
  <div class="app">
    <NavBar/>
    <LandingPage/>

    <div class='section-container'>
      <h1 class='section-title'>A complete messaging experience.</h1>
      <div class='section-subtitle'>
        Amity is an interactive messaging app that brings everything together,
        and introduces a new level of live human interaction. All in one place.
      </div>
    </div>


    <div class='section2-container section-container'>
      <h1 class='section-title'>Interact freely with Live Mode.</h1>
      <div class='section-subtitle'>
        Special features will activate when two or more people are together on the
        same screen. Express yourself with live emojis, live touch, and emoji bursts.
      </div>
      <div class='iphone-container'>
        <phoneCase v-bind:video="videos.live1"/>
        <phoneCase v-bind:video="videos.live2"/>
      </div>
    </div>

    <VideoBackgroundTwo/>

    <div class='section3-container section-container'>
      <div class='section3-items'>
        <h2 class='section-title'>
          Send anything, instantly.<br/>
          Without leaving the app.
        </h2>
        <div class='section-subtitle'>
          You can send photos, videos, links, news, locations,
          YouTube videos, voice messages, thought messages,
          battery levels, stickers, and more - all within Amity.
        </div>
      </div>
      <div class='section3-items'>
        <div class='iphone-container'>
          <PhoneCase v-bind:video="videos.live3"/>
        </div>
      </div>
    </div>

    <div class='section4-container section3-container section-container'>
      <div id='section4-desktop-only' class='section3-items'>
        <div class='iphone-container'>
          <PhoneCase v-bind:video="videos.live4"/>
        </div>
      </div>
      <div class='section3-items'>
        <h2 class='section-title'>
          Interactive messages.<br/>Tap to request photo.
        </h2>
        <div class='section-subtitle'>
          Thinking of someone? Now you can just tap one button
          to ask anyone for a photo, video, or even their location.
          Starting conversations in Amity is easier, and more fun.
        </div>
      </div>
      <div id='section4-mobile-only' class='section3-items'>
        <div class='iphone-container'>
          <PhoneCase v-bind:video="videos.live4"/>
        </div>
      </div>
    </div>


    <div class='section5-container section3-container section-container'>
      <div class='section3-items'>
        <h2 class='section-title'>
          All your memories.<br/>
          Saved automatically.
        </h2>
        <div class='section-subtitle'>
          All the photos, videos, links, news articles, YouTube
          videos, and postcards you send and receive are saved
          and organised in one place. Tap to revisit anytime.
        </div>
      </div>
      <div class='section3-items'>
        <div class='iphone-container'>
          <PhoneCase v-bind:video="videos.live5"/>
        </div>
      </div>
    </div>

    <FooterLinks/>

  </div>
</template>



<script>
import LandingPage from './components/LandingPage.vue'
import ListPage from './components/ListPage.vue'
import CreatePost from './components/CreatePost.vue'
import Nav from './components/Nav.vue'
import PhoneCase from './components/PhoneCase.vue'
import VideoBackgroundTwo from './components/VideoBackgroundTwo.vue'
import FooterLinks from './components/Footer.vue'



export default {
  name: 'app',
  data: () => ({
    test: 'testing',
    videos: {
      live1: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSourceWEBM: "https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/left.webm",
        videoSourceMP4: "https://d129oov5pfixbg.cloudfront.net/video/left.mp4",
      },
      live2: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSourceWEBM: "https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/right.webm",
        videoSourceMP4: "https://d129oov5pfixbg.cloudfront.net/video/right.mp4",
      },
      live3: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSourceWEBM: "https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/interactivenewest.webm",
        videoSourceMP4: "https://d129oov5pfixbg.cloudfront.net/video/interactivenewest.mp4",
      },
      live4: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSourceWEBM: "https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/interactive.webm",
        videoSourceMP4: "https://d129oov5pfixbg.cloudfront.net/video/interactive.mp4",
      },
      live5: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSourceWEBM: "https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/memories.webm",
        videoSourceMP4: "https://d129oov5pfixbg.cloudfront.net/video/memories.mp4",
      },
    }
  }),
  components: {
    'NavBar': Nav,
    'LandingPage': LandingPage,
    'Feed': ListPage,
    'Create': CreatePost,
    'PhoneCase': PhoneCase,
    'VideoBackgroundTwo': VideoBackgroundTwo,
    'FooterLinks': FooterLinks,
  },
  created () {
  },
  destroyed () {
  }
}
</script>



<style lang='sass'>

/* latin-ext */
@font-face {
  font-family: 'Lato';
  font-style: normal;
  font-weight: 300;
  src: local('Lato Light'), local('Lato-Light'), url(https://fonts.gstatic.com/s/lato/v13/IY9HZVvI1cMoAHxvl0w9LVKPGs1ZzpMvnHX-7fPOuAc.woff2) format('woff2');
  unicode-range: U+0100-024F, U+1E00-1EFF, U+20A0-20AB, U+20AD-20CF, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: 'Lato';
  font-style: normal;
  font-weight: 300;
  src: local('Lato Light'), local('Lato-Light'), url(https://fonts.gstatic.com/s/lato/v13/22JRxvfANxSmnAhzbFH8PgLUuEpTyoUstqEm5AMlJo4.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215;
}
$navbarHeight: 60px;

html {
  box-sizing: border-box;
  font-weight: 300;
}

*, *:before, *:after {
  box-sizing: inherit;
}


body, input, button {
  font-family: Lato, Helvetica, sans-serif;
  font-size: 16pt;
  margin: 0px;
  padding: 0px;
  background-color: #fff;
}

a {
  color: #E0C082;
  text-decoration: none;
}

button {
  color: #fff;
  background-color: #E0C082;
}

ul li {
  list-style: none;
}
</style>

<style lang='sass'>
.app {
  overflow-x: hidden;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: auto;
}

.section-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 10% 15% 10%;
  background-color: #fff;
}
.section-title {
  color: #444;
  font-weight: 300;
  line-height: 2.6rem;
}

.section-subtitle {
  font-weight: 300;
  line-height: 2rem;
  color: #999;
  padding-bottom: 5%;
}

.section2-container {
  background-color: #f9f9f9;
  padding: 10% 15% 0%;
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  .section2-container {
    padding: 10% 5% 0%;
  }
}

.section3-container {
  flex-direction: row;
  flex-wrap: wrap;
  background-color: #fff;
  padding: 10% 10% 0%;
}
.section3-items {
  flex: 1 1 50%;
  flex-basis: 350px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.section4-container {
  background-color: #f9f9f9;
}

#section4-desktop-only {
  display: block;
}
#section4-mobile-only {
  display: none;
}

@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  #section4-desktop-only {
    display: none;
  }
  #section4-mobile-only {
    display: block;
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  #section4-desktop-only {
    display: none;
  }
  #section4-mobile-only {
    display: block;
  }
}
</style>

<style lang='sass'>
.iphone-container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: space-around;
}


input:focus {
  box-shadow: none;
  outline: none;
  border-color: #40b883;
}

input {
  padding: 8px;
  border: solid 1px #bbb;
  border-radius: 2px;
}

</style>


