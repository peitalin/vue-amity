
<template>
  <div>
    <form  id="download-form" class="fv-form fv-form-bootstrap" name="phoneform" method="post" action="post.php" data-fv-framework="bootstrap4" data-fv-icon-valid="fa fa-check" data-fv-icon-invalid="fa fa-times" data-fv-icon-validating="fa fa-refresh" novalidate="novalidate" _lpchecked="1">

      <div class="download-link">Get a free download link sent to your phone.</div>
      <button type="submit" class="fv-hidden-submit" style="display: none; width: 0px; height: 0px;"></button>

      <div class="form-group" style="display:none;">
          <label>Name</label>
          <input type="text" name="name" class="form-control" value="">
      </div>

      <div class="form-group has-feedback has-success">
        <input id="output" class="form-control" type="text" name="output" value="" style="display:none;">
        <input id="submit-link" class="text-link" type="submit" name="upviralsubmit" value="Text me the link">
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
</template>


<script>
</script>


<style lang='sass'>

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

