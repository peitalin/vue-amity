

<template>
  <div class='landing-page-hero'>
    <div class='landing-container'>

      <video playsinline autoplay muted loop poster="https://d129oov5pfixbg.cloudfront.net/img/previewbro.jpg" id="videobg">
        <!-- <source src="https://d129oov5pfixbg.cloudfront.net/video/comp-tiny2.mp4" type="video/mp4"> -->
        <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.webm" type="video/webm">
        <source src="https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/comp-nano2.mp4" type="video/mp4">
        <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.m4v" type="video/m4v">
        <source src="https://d129oov5pfixbg.cloudfront.net/video/vid1.ogv" type="video/ogg">
      </video>

      <div class="black-overlay"></div>


      <div class='form-container'>
        <div class='form-first-block'>
          <img class="amitylogo" src="https://d129oov5pfixbg.cloudfront.net/img/amity-desktop.svg">
          <div class="main-form">
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
          <div class="download-link">Get a free download link sent to your phone.</div>

          <form class="fv-form fv-form-bootstrap" name="phoneform" id="mainemailform" method="post" action="post.php" data-fv-framework="bootstrap4" data-fv-icon-valid="fa fa-check" data-fv-icon-invalid="fa fa-times" data-fv-icon-validating="fa fa-refresh" novalidate="novalidate" _lpchecked="1">
            <button type="submit" class="fv-hidden-submit" style="display: none; width: 0px; height: 0px;"></button>

            <div class="form-group" style="display:none;">
                <label>Name</label>
                <input type="text" name="name" class="form-control" value="">
            </div>

            <div class="form-group has-feedback has-success">
              <input id="output" type="text" name="output" class="form-control" value="" style="display:none;">
              <input type="submit" name="upviralsubmit" id="submit-link" class="text-link" value="Text me the link">
              <small class="help-block" data-fv-validator="callback" data-fv-for="phoneNumber" data-fv-result="VALID" style="display: none;">
                The phone number is not valid. Please try again.
              </small>
            </div>
            <br/>
            <input type="hidden" name="upviralsubmit" data-fv-submit-hidden="" value="Text me the link">
          </form>

          <div class='appstores'>
            <a class='appstores-link' href="https://itunes.apple.com/app/id1125299418">
              <img id='applestore' src="https://upload.wikimedia.org/wikipedia/commons/3/3c/Download_on_the_App_Store_Badge.svg"><br><span></span>
            </a>
            <a class='appstores-link' href="https://play.google.com/store/apps/details?id=com.amity.amity.beta">
              <img id='playstore' src="https://upload.wikimedia.org/wikipedia/commons/c/cd/Get_it_on_Google_play.svg"><br><span>(Beta)</span>
            </a>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>



<script>
</script>



<style lang='sass'>

.amitylogo {
  margin-top: 20vh;
  margin-bottom: 5%;
  max-height: 25vh;
  width: 66vw;
  max-width: 400px;
}

@media screen {
  .form-container {
    display: flex;
    flex-direction: column;
  }
  .form-first-block {
    margin-bottom: 7%;
  }
  .appstores {
    display: flex;
    flex-wrap: wrap;
    flex: 1 1 50%;
    justify-content: center;
  }
}

@media screen and (device-aspect-ratio: 9/16) {
  .form-container {
    display: flex;
    flex-direction: column;
  }
  .form-first-block {
    margin-bottom: 7%;
  }
  .appstores {
    display: block;
  }
}

@media screen and (device-aspect-ratio: 16/9) {
  .amitylogo {
    margin-bottom: 0%;
  }
  .form-container {
    display: flex;
    flex-direction: row;
  }
  .form-first-block {
    width: 55vw;
    padding-left: 5%;
    padding-top: 2%;
  }
  .form-second-block {
    width: 45vw;
    margin-top: 20%;
    padding-right: 5%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .appstores {
    display: flex;
    justify-content: space-around;
  }
}

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

.videobg-spacer {
  height: 100vh;
  background-color: #fff;
  z-index: -101;
}

.main-form {
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


.download-link {
  color: #fff;
  font-size: 0.8em;
  font-weight: 400;
  margin: 2%;
}

input#submit-link.text-link {
  color: #fff;
  border: 1px solid #aaa;
  border-radius: 5px;
  background-color: #222;
  transition: all 0.2s ease;
}
input#submit-link.text-link:hover {
  color: #222;
  border: 1px solid #fff;
  background-color: #E0C082;
  transition: all 0.2s ease;
}
input#submit-link.text-link:active {
  color: #222;
  border: 1px solid #fff;
  background-color: #E0C082;
  transition: all 0.2s ease;
}

.appstores-link {
  height: 30px;
}
#applestore {
  width: 20vw;
  min-width: 140px;
  max-width: 180px;
}
#playstore {
  width: 20vw;
  min-width: 140px;
  max-width: 180px;
}

</style>
