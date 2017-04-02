
<template>
  <div>

    <div class='mobile-form-container'>
      <div class="mobile-form-input">
        <input class='mobile-number-input' id="mobile-number-input" type="tel">
        <br/>
        <button id="mobile-number-submit"> Text me the link </button>
        <br/>
        <span id="valid-msg" class="hide-validation-response">Done! We've sent an SMS to your phone.</span>
        <span id="error-msg" class="hide-validation-response">The phone number is not valid. Please try again.</span>
      </div>
    </div>


    <div class='appstores'>
      <a class='appstores-link' href="https://itunes.apple.com/app/id1125299418">
        <img id='applestore' src="https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/apple-store.svg"><br><span></span>
      </a>
      <a class='appstores-link' href="https://play.google.com/store/apps/details?id=com.amity.amity.beta">
        <img id='playstore' src="https://s3-ap-southeast-2.amazonaws.com/amitylandingpage/google-play-store.svg"><br><span>(Beta)</span>
      </a>
    </div>

  </div>
</template>


<script>
import FormSignUps from './FormSignUps.vue'

export default {
  data: () => ({
    select: '',
  }),
  components: {
  },
  methods: {
  },
  mounted () {
    // select all .mobile-number-input elements
    var telInput = $("#mobile-number-input");
    var errorMsg = $("#error-msg");
    var validMsg = $("#valid-msg");

    // initialise plugin
    // lookup user's country
    telInput.intlTelInput({
      initialCountry: "auto",
      separateDialCode: true,
      geoIpLookup: function(callback) {
        $.get('http://ipinfo.io', function() {}, "jsonp").always(function(resp) {
          var countryCode = (resp && resp.country) ? resp.country : "";
          callback(countryCode);
        });
      },
      utilsScript: "../../node_modules/intl-tel-input/build/js/utils.js" // just for formatting/placeholders etc
    });

    var reset = () => {
      telInput.removeClass("error");
      errorMsg.addClass("hide-validation-response");
      validMsg.addClass("hide-validation-response");
    };

    // on blur: validate
    telInput.blur(() => {
      reset();
      if ($.trim(telInput.val())) {
        if (telInput.intlTelInput("isValidNumber")) {
          validMsg.removeClass("hide-validation-response");
        } else {
          telInput.addClass("error");
          errorMsg.removeClass("hide-validation-response");
        }
      }
    });
    // on keyup / change flag: reset
    telInput.on("keyup change", reset);
  },
  destroyed () {
  }
}
</script>



<style>
.mobile-form-container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
}
.mobile-form-input {
  margin-bottom: 2%;
}
.mobile-form {
}
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  // portrait mode on mobile
  .mobile-form-container {
    display: none;
  }
  .selected-dial-code {
    display: none !important;
    /* override intlTelInput.css */
  }
  .iti-flag {
    display: none !important;
    /* override intlTelInput.css */
  }
  .iti-arrow {
    display: none !important;
    /* override intlTelInput.css */
  }
  #mobile-number-input {
    display: none;
  }
  #mobile-number-submit {
    display: none;
  }
}
@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  // landscape mode on mobile
  .mobile-form-container {
    display: none;
  }
  .selected-dial-code {
    display: none !important;
    /* override intlTelInput.css */
  }
  .iti-flag {
    display: none !important;
    /* override intlTelInput.css */
  }
  .iti-arrow {
    display: none !important;
    /* override intlTelInput.css */
  }
  #mobile-number-input {
    display: none;
  }
  #mobile-number-submit {
    display: none;
  }
}
#mobile-number-input {
  width: 32vw;
  min-width: 140px;
  max-width: calc(160px * 2);
  border-radius: 6px;
  font-weight: 700;
  font-size: 0.9em;
}
#mobile-number-submit:hover {
  background: #53bdff;
}
#mobile-number-submit {
    text-align: center;
    font-size: 18px;
    height: 48px;
    border-radius: 6px;
    border: none;
    margin-top: 11px;
    font-weight: 700;
    color: #fff;
    background: #40b5ff;
    transition: 0.3s;
    width: 32vw;
    min-width: 140px;
    max-width: calc(160px * 2);
}
#valid-msg {
  background: rgba(0,0,0,0);
  color: #4f4;
  font-size: 1rem;
}
#error-msg {
  background: rgba(0,0,0,0);
  color: #f44;
  font-size: 1rem;
}
.hide-validation-response {
  display: none;
  transition: all 0.5s ease;
}
.selected-flag {
  font-size: 0.8em !important;
  font-weight: 700 !important;
  /* override intTelInput.css */
}
.selected-dial-code {
  padding-left: 8px !important;
  /* override intTelInput.css */
}
</style>



<style lang='sass'>
.country-drop-down {
  width: 20vw;
}

.form-container {
  display: flex;
  flex-direction: column;
  transition: all 0.1s ease;
}
.form-first-block {
  margin-bottom: 2%;
  transition: all 0.1s ease;
}
.form-second-block {
  transition: all 0.1s ease;
}
.appstores {
  display: flex;
  flex-wrap: wrap;
  flex: 1 1 50%;
  justify-content: center;
  transition: all 0.1s ease;
}

@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  // portrait mode on mobile
  .form-container {
    display: flex;
    flex-direction: column;
  }
  .form-first-block {
    margin-bottom: 5%;
  }
  #download-form {
    display: none;
    visibility: hidden;
  }
  .appstores {
    display: block;
  }
}

@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  // landscape mode on mobile
  .form-container {
    display: flex;
    flex-direction: row;
  }
  .form-first-block {
    width: 60vw;
    padding-left: 5%;
    padding-top: 2%;
  }
  .form-second-block {
    width: 40vw;
    padding-top: 30vh;
    padding-right: 5%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  #download-form {
    display: none;
    visibility: hidden;
  }
  .appstores {
    display: block;
  }
}
</style>

<style lang='sass'>
#download-form {
  margin-bottom: 0px;
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
  background-color: rgba(0,0,0,1);
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

input#submit-link {
  min-width: 110px;
  max-width: 160px;
  font-size: .8em;
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
  transform: scale(1.04);
  transition: transform 0.2s ease;
}
#applestore:active {
  transform: scale(1.04);
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
