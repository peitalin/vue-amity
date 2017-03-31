
<template>
  <div class="videobg2-container">

    <video id='videobg2' playsinline autoplay muted loop poster="https://d129oov5pfixbg.cloudfront.net/img/high5preview.jpg">
      <source src="https://d129oov5pfixbg.cloudfront.net/video/high5.mp4" type="video/mp4">
    </video>

    <div class="videobg2-content">
      <div class="videobg2-content-inner">
          <h2 id="videobg2-title" class="section-title">Celebrate anytime with <br class="onlymobile">High Fives.</h2>
          <div id="videobg2-subtitle" class="section-subtitle">A first-of-its-kind interactive message that allows you to celebrate<br class="nomobile"> moments with friends throughout the day in real-time.</div>
      </div>
    </div>

  </div>
</template>

<style>
.videobg2-container {
  position: relative;
  height: 66vh;
}
.videobg2-content {
  margin: 10vh;
  border: 1px solid #eee;
  height: calc(66vh - 20vh);
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  .videobg2-container {
    height: 100vh;
  }
  .videobg2-content {
    height: calc(100vh - 20vh);
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  .videobg2-container {
    height: 100vh;
  }
  .videobg2-content {
    height: calc(100vh - 20vh);
  }
}

.videobg2-content-inner {
  background-color: rgba(0,0,0,0.4);
  height: 100%;
  color: #eee;
  font-weight: 400;
  line-height: 2rem;
  padding: 5%;
}
#videobg2-title {
  color: #eee;
}
#videobg2-subtitle {
  color: #eee;
}
video#videobg2 {
  z-index: -1;
  position: absolute;
  left: 0;
  top: 0;
  min-width: 100vw;
  height: auto;
}
</style>

<script>
export default {
  data: () => ({
    allPosts: {},
    loading: 0,
  }),
  components: {
  }
}
</script>
