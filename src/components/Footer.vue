
<template>
  <div class='footer-container'>
    <div class='footer-signup'>

      <!-- same code as formsignups.vue, must duplciate since intlTelInput  -->
      <!-- can't generate second instance  -->
      <div class='mobile-form-container'>
        <div class="mobile-form-input">
          <input class='mobile-number-input' id="mobile-number-input2" type="tel">
          <br/>
          <button id="mobile-number-submit"> Text me the link </button>
          <br/>
          <span id="valid-msg2" class="hide-validation-response">Done! We've sent an SMS to your phone.</span>
          <span id="error-msg2" class="hide-validation-response">The phone number is not valid. Please try again.</span>
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

    <div class='footer-rights'>
      <div class='copyright'>Copyright © 2017 Amity. All Rights Reserved.</div>
      <br/>
      <div class='footer-links'>
        <ul>
          <li><a href="https://amity.io/terms.php">Terms</a> <span>|&nbsp;</span> </li>
          <li><a href="https://amity.io/privacy.php">Privacy</a> <span>|&nbsp;</span> </li>
          <li><a href="http://bit.ly/amity-media-kit-website">Press Kit</a> <span>|&nbsp;</span> </li>
          <li><a href="mailto:hello@amity.io">Email</a></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import FormSignUps from './FormSignUps.vue'

export default {
  data: () => ({
  }),
  components: {
    "FormSignUps": FormSignUps,
  },
  mounted () {
    // select all .mobile-number-input elements
    var telInput = $("#mobile-number-input2");
    var errorMsg = $("#error-msg2");
    var validMsg = $("#valid-msg2");

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
  },
}
</script>

<style lang='sass'>

#mobile-number-input2 {
  width: 32vw;
  min-width: 140px;
  max-width: calc(160px * 2);
  border-radius: 6px;
  font-weight: 700;
  font-size: 0.9em;
}
#valid-msg2 {
  background: rgba(0,0,0,0);
  color: #4f4;
  font-size: 1rem;
}
#error-msg2 {
  background: rgba(0,0,0,0);
  color: #f44;
  font-size: 1rem;
}
.footer-container {
}
.footer-signup {
 background-color: #1E2023;
 padding: 5%;
}
.footer-rights {
  color: #46474A;
  background-color: #1A1C1F;
  padding-top: 2%;
  padding-bottom: 2%;
  font-size: 1rem;
  height: 100%;

  .copyright {
    position: absolute;
    display: inline;
    left: 0;
    padding-left: 2%;
  }

}
.footer-links {

  ul {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    padding-left: 2%;
    margin: 1% 0 1%;
  }

  li a {
    color: #6A6B6D;
  }

  li a:hover {
    color: #E0C082;
  }
}
</style>

