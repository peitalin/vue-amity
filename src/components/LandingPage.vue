

<template>
  <div class='landing-page-hero'>

    <transition name="fade">
      <div v-if="playVideo" v-bind:class="['modalVideo', halfScreen ? 'modalVideo-halfscreen' : 'modalVideo-fullscreen']">
        <iframe src="https://www.youtube.com/embed/ngBrlY2g0IM?autoplay=1&rel=0"></iframe>
        <!-- <div v-on:click="playVideo = false" class="closeModalVideo"></div> -->
      </div>
    </transition>

    <transition name="fade">
      <div v-if="!halfScreen && (playVideo)">
          <div class='modalVideo-navbar'></div>
          <div class='modalVideo-navbar-bottom'></div>
      </div>
    </transition>

    <div class='landing-container'>

      <div class='overflow-relative'>
        <video id='videobg' playsinline autoplay muted loop poster="https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg">
          <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.webm" type="video/webm">
          <source src="https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/comp-nano2.mp4" type="video/mp4">
          <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.m4v" type="video/m4v">
          <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.ogv" type="video/ogg">
        </video>
      </div>

      <div class="black-overlay">
        <div class="black-overlay-inner-border">
        </div>
      </div>


      <div class='form-container'>
        <div class='form-first-block'>

          <div v-bind:class="[playVideo ? hide : '']">
            <img class="amitylogo" src="https://d129oov5pfixbg.cloudfront.net/img/amity-desktop.svg">
          </div>

          <div class="video-play-container">
            <a v-on:click="playVideo = !playVideo" class="video-play" data-toggle="modal" data-target="#videoModal" data-thevideo="//www.youtube.com/embed/ngBrlY2g0IM">

              <!-- hide main play button when video is playing -->
              <div v-bind:class="[playVideo ? hide : '', 'relativeSVG']">
                <svg class="video-play-button-svg" viewBox="0 0 200 200" alt="Play video">
                  <circle cx="100" cy="100" r="90" fill="rgba(0,0,0,0.3)" stroke-width="6" stroke="#ddd"/>
                  <polygon points="70, 55 70, 145 145, 100" fill="#ddd" stroke-width="6"/>
                </svg>
              </div>

              <!-- show close button  when playing: top-left when scrollY > window.innerHeight/10, center otherwise -->
              <div v-bind:class="['fixedSVG', !playVideo ? hide : '', halfScreen ? 'button-center' : 'button-top-left']">
                <svg class="video-play-button-svg" viewBox="0 0 200 200" alt="Play video">
                  <circle cx="100" cy="100" r="90" fill="rgba(0,0,0,0.3)" stroke-width="10" stroke="#ddd"/>
                  <line x1="60" y1="60" x2="140" y2="140" stroke-width="10" stroke="#ddd"/>
                  <line x1="60" y1="140" x2="140" y2="60" stroke-width="10" stroke="#ddd"/>
                </svg>
              </div>

              <div class="video-play-button-text">
                <div v-bind:class="[playVideo ? inactiveClass : '']">
                    Watch the video
                </div>
              </div>
            </a>
          </div>
        </div>

        <div class='form-second-block'>
          <transition name="fade">
            <div v-if='!playVideo'>
              <FormSignUps/>
            </div>
          </transition>
        </div>
      </div>


    </div>
  </div>
</template>



<script>
import FormSignUps from './FormSignUps.vue'

export default {
  data: () => ({
    playVideo: false,
    hide: 'hide',
    fixedSVG: 'fixedSVG',
    scrollY: 0,
    window: window,
    halfScreen: false,
  }),
  components: {
    'FormSignUps': FormSignUps,
  },
  methods: {
    togglePlayVideo: () => {
      return !this.playVideo
    },
    handleScroll () {
      this.scrollY = window.scrollY;
      this.halfScreen = (scrollY > window.innerHeight/10);
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style lang='sass'>
.modalVideo {
  z-index: 2;
}
.modalVideo-navbar {
  position: fixed;
  color: #E0C082;
  z-index: 5;
  width: 100vw;
  height: 60px;
  padding: 2%;
  background: rgba(0,0,0,0.9);
}
.modalVideo-navbar-bottom {
  position: fixed;
  color: #E0C082;
  width: 100vw;
  height: 60px;
  padding: 2%;
  bottom: 0;
  background: rgba(0,0,0,0.9);
  animation: temporary-hide-play-controls 4s;
  animation-iteration-count: 1;
}
@keyframes temporary-hide-play-controls {
  0% {
    opacity: 0;
    z-index: 0;
  }
  25% {
    opacity: 1;
    z-index: 5;
  }
  75% {
    opacity: 1;
    z-index: 5;
  }
  100% {
    opacity: 0;
    z-index: 0;
  }
}

.closeModalVideo {
  background-color: rgba(0,0,0,0.8);
  height: 100vh;
  width: 100vw;
  z-index: 2;
}
.modalVideo-halfscreen {
  position: fixed;
  width: 100vw;
  height: 50vh;
  border: 0px solid #222;
  transition: all 0.6s ease;
}
.modalVideo-fullscreen {
  position: fixed;
  width: 100vw;
  height: 100vh;
  border: 0px solid #222;
  transition: all 0.6s ease;
}
iframe {
  width: 100%;
  height: 100%;
  border: 0px solid #222;
  background: rgba(0,0,0,0.8);
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  // portrait mode on mobile
  .modalVideo-halfscreen {
    position: fixed;
    width: 100vw;
    height: 25vh;
    border: 0px solid #222;
    transition: all 0.6s ease;
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  // landscape mode on mobile
}
</style>


<style lang='sass'>
.overflow-relative {
  position: relative;
}
video#videobg {
  position: absolute;
  top: 50vh;
  left: 50vw;
  min-height: 100vh;
  min-width: 100vw;
  width: auto;
  z-index: -99;
  -ms-transform: translate3d(-50%, -50%, 0);
  -moz-transform: translate3d(-50%, -50%, 0);
  -webkit-transform: translate3d(-50%, -50%, 0);
  transform: translate3d(-50%, -50%, 0);
  background: url(https://d129oov5pfixbg.cloudfront.net/video/vid1.webm) no-repeat;
  background-size: auto auto;
}

.amitylogo {
  margin-top: 20vh;
  margin-bottom: 2%;
  max-height: 25vh;
  width: 66vw;
  max-width: 400px;
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  // portrait mode on mobile
  .amitylogo {
    margin-top: 25vh;
  }
  video#videobg {
    height: 100vh;
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  // landscape mode on mobile
  .amitylogo {
    margin-bottom: 0%;
  }
  video#videobg {
    height: 100vh;
  }
}

</style>


<style lang='sass'>
.landing-page-hero {
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

.fade-enter-active, .fade-leave-active {
  opacity: 1;
  transition: opacity .8s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
  transition: opacity .8s;
  transition-delay: 0.0s;
}
.hide {
  opacity: 0;
  transition: opacity 0.2s ease;
}
.fixedSVG {
  position: fixed;
  transform: scale(0.6);
  transition: all 0.4s ease;
  z-index: 5;
}
.relativeSVG {
  position: relative;
  transform: scale(1);
  transition: all 0.4s ease;
  z-index: 0;
}
.button-top-left {
  left: 1vw;
  top: 1vh;
}
.button-center {
  left: 46%;
  top: 45.5%;
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  // portrait mode on mobile
  .button-top-left {
    left: -2%;
    top: -2%;
  }
  .button-center {
    left: 40vw;
    top: calc(25vh - 38px);
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  // landscape mode on mobile
  .button-top-left {
    left: -1%;
    top: -2%;
  }
  .button-center {
    left: 46%;
    top: 41%;
  }
}

</style>



<style lang='sass'>
.black-overlay {
  position: absolute;
  z-index: -99;
  top: 0;
  left: 0;
  min-width: 100vw;
  min-height: 100vh;
  width: auto;
  height: auto;
  background: rgba(0, 0, 0, 0.50);
}

.black-overlay-inner-border {
  height: calc(100vh - 20vh);
  border: 1px solid #999;
  background: rgba(0,0,0,0.4);
  margin: 10vh;
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  .black-overlay-inner-border {
    height: calc(100vh - 10vh);
    margin: 5vh;
  }
}

@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  .black-overlay-inner-border {
    height: calc(100vh - 10vh);
    margin: 5vh;
  }
}

.videobg-spacer {
  height: 100vh;
  background-color: #fff;
  z-index: -101;
}

.video-play-container {
  display: flex;
  justify-content: center;
  max-width: 100vw;
}

svg.video-play-button-svg {
  z-index: 2;
  height: 20vh;
  max-height: 60px;
  width: 20vw;
  max-width: 60px;
  margin-top: 10%;
  transform: scale(0.8);
  transition: transform 0.2s ease;
}
svg.video-play-button-svg:hover {
  transform: scale(1);
  transition: transform 0.2s ease-in-out;
}
.video-play-button-text {
  color: #eee;
}
</style>


<style lang='sass'>
.appstores-link {
  color: #eee;
}
.appstores-link:hover {
  color: #E0C082;
}
#applestore {
  width: 16vw;
  min-width: 140px;
  max-width: 160px;
  transition: transform 0.2s ease;
}
#applestore:hover {
  transform: scale(1.05);
  transition: transform 0.2s ease;
}
#applestore:active {
  transform: scale(1.05);
  transition: transform 0.2s ease;
}
#playstore {
  width: 16vw;
  min-width: 140px;
  max-width: 160px;
  transition: transform 0.2s ease;
}
#playstore:hover {
  transform: scale(1.05);
  transition: transform 0.2s ease;
}
#playstore:active {
  transform: scale(1.05);
  transition: transform 0.2s ease;
}
</style>
