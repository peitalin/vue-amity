
<template>
  <div class="app">
    <navBar/>
    <landingPage/>

    <div class='copy-container'>
      <h1 class='copy-title'>A complete messaging experience.</h1>
      <div class='copy-subtitle'>Amity is an interactive messaging app that brings everything together,
and introduces a new level of live human interaction. All in one place.</div>
    </div>

    <div class='copy-container copy2-container'>
      <h1 class='copy-title'>Interact freely with Live Mode.</h1>
      <div class='copy-subtitle'>Special features will activate when two or more people are together on the
same screen. Express yourself with live emojis, live touch, and emoji bursts.</div>
      <div class='iphone-container'>
        <phoneCase v-bind:video="videos.live1"/>
        <phoneCase v-bind:video="videos.live2"/>
      </div>
    </div>

    <div style="z-index:2; background-color: #fff; padding: 10%;">
      <feed/>
      <create/>
    </div>
  </div>
</template>


<script>
import LandingPage from './components/LandingPage.vue'
import ListPage from './components/ListPage.vue'
import CreatePost from './components/CreatePost.vue'
import Nav from './components/Nav.vue'
import PhoneCase from './components/PhoneCase.vue'


export default {
  name: 'app',
  data: () => ({
    test: 'testing',
    videos: {
      live1: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSource: "https://d129oov5pfixbg.cloudfront.net/video/left.mp4"
      },
      live2: {
        videoPoster: "https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg",
        videoSource: "https://d129oov5pfixbg.cloudfront.net/video/right.mp4"
      },
    }
  }),
  components: {
    'navBar': Nav,
    'landingPage': LandingPage,
    'feed': ListPage,
    'create': CreatePost,
    'phoneCase': PhoneCase,
  },
}
</script>



<style lang='sass'>

@import url(https://fonts.googleapis.com/css?family=Open+Sans:400|Raleway:300);
$navbarHeight: 60px;

html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}

body, input, button {
  font-family: Raleway, Open Sans, Helvetica, sans-serif;
  font-size: 16pt;
  margin: 0px;
  padding: 0px;
  overflow-x: hidden;
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

.app {
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: auto;
}

.copy-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 10% 15% 10%;
  background-color: #fff;
}
.copy-title {
  color: #444;
  font-weight: 400;
  line-height: 36px;
}

.copy-subtitle {
  font-weight: 400;
  line-height: 36px;
  color: #999;
  padding-bottom: 5%;
}

.copy2-container {
  background-color: #f9f9f9;
  padding: 10% 15% 0%;
}

.iphone-container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: space-between;
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
