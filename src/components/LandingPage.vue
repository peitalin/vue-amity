

<template>
  <div class='landing-page-hero'>
    <div class='landing-container'>

      <video id='videobg' playsinline autoplay muted loop poster="https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg">
        <!-- <source src="https://d129oov5pfixbg.cloudfront.net/video/comp-tiny2.mp4" type="video/mp4"> -->
        <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.webm" type="video/webm">
        <source src="https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/comp-nano2.mp4" type="video/mp4">
        <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.m4v" type="video/m4v">
        <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.ogv" type="video/ogg">
      </video>

      <div class="black-overlay">
        <div class="black-overlay-inner-border"></div>
      </div>


      <div class='form-container'>
        <div class='form-first-block'>
          <img class="amitylogo" src="https://d129oov5pfixbg.cloudfront.net/img/amity-desktop.svg">
          <div class="video-play-container">
            <a class="video-play" data-toggle="modal" data-target="#videoModal" data-thevideo="//www.youtube.com/embed/ngBrlY2g0IM">
              <svg class="video-play-button-svg" viewBox="0 0 200 200" alt="Play video">\
                <circle cx="100" cy="100" r="90" fill="rgba(0,0,0,0.3)" stroke-width="5" stroke="#eee"/>\
                <polygon points="70, 55 70, 145 145, 100" fill="#eee"/>\
              </svg>
              <div class="video-play-button-text">
                Watch the video
              </div>
            </a>
          </div>
        </div>

        <div class='form-second-block'>

          <FormSignUps/>

        </div>
      </div>

    </div>
  </div>
</template>



<script>
import FormSignUps from './FormSignUps.vue'

export default {
  data: () => ({
    loading: 0,
  }),
  components: {
    'FormSignUps': FormSignUps,
  }
}
</script>




<style lang='sass'>
.landing-page-hero {
  height: 100vh;
  width: 100vw;
  overflow-x: hidden;
}

video#videobg {
  position: absolute;
  top: 50vh;
  left: 50vw;
  min-width: 100vw;
  min-height: 100vh;
  width: auto;
  height: auto;
  z-index: -100;
  -ms-transform: translate3d(-50%, -50%, 0);
  -moz-transform: translate3d(-50%, -50%, 0);
  -webkit-transform: translate3d(-50%, -50%, 0);
  transform: translate3d(-50%, -50%, 0);
  background: url(https://d129oov5pfixbg.cloudfront.net/video/vid1.webm) no-repeat;
  background-size: cover;
}

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

.video-play-button-svg {
  height: 20vh;
  max-height: 60px;
  width: 20vw;
  max-width: 60px;
  margin-top: 10%;
  transform: scale(1);
  transition: transform 0.2s ease;
}
.video-play-button-svg:hover {
  transform: scale(1.1);
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
