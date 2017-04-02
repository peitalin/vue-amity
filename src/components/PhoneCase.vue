
<template>
  <div class="phonecase">
    <video v-bind:poster="video.videoPoster" id='iphone-video' autoplay muted playsinline loop>
      <source v-bind:src="video.videoSourceWEBM" type="video/webm" />
      <source v-bind:src="video.videoSourceMP4" type="video/mp4">
      <!-- <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.m4v" type="video/m4v" /> -->
      <!-- <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.ogv" type="video/ogg" /> -->
    </video>
  </div>
</template>

<script>
export default {
  props: ["video"],
}
</script>


<style lang="sass">


:root {
  --phone-case-height: 55vw;
  --video-scale-height: 0.82;
  --phone-case-width: calc(0.58333333 * var(--phone-case-height));
  --video-scale-width: 0.82;
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  // portrait mode on mobile
  :root {
    --phone-case-height: 66vw;
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  // landscape mode on mobile
  :root {
    --phone-case-height: 55vw;
  }
}

.phonecase {
    background: url(https://amity.io/img/holder.png) no-repeat;
    background-size: var(--phone-case-width);
    height: var(--phone-case-height);
    width: var(--phone-case-width);
    text-align: center;
    padding-top: calc(0.152 * var(--phone-case-height));
    margin-left: 2px;
}

video#iphone-video {
  width: calc(var(--video-scale-width) * var(--phone-case-width));
  height: calc(var(--video-scale-height) * var(--phoneCase-height));
}

@media screen and (min-width: 1080px) {
  .phonecase {
      background: url(https://amity.io/img/holder.png) no-repeat;
      height: 600px;
      width: 350px;
      text-align: center;
      padding-top: 91px;
      margin-left: 2px;
  }
  video#iphone-video {
    height: 508px;
    width: 290px;
  }
}

</style>
