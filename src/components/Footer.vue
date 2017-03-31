
<template>
  <div class='footer-container'>
    <div class='footer-signup'>
      <FormSignUps/>
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
  }
}
</script>

<style lang='sass'>
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

