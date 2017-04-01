
<template>
  <nav v-bind:class="[(scrollY < (htmlHeight - window.innerHeight - 50)) ? 'hide-nav' : 'nav-bar' ]">
    <!-- <div style='position:fixed; color:#aaa; left:50px; top:20px;'> -->
    <!--   ScrollY: {{ scrollY < window.innerHeight }} -->
    <!-- </div> -->
    <div class='nav-inside'>
      <ul>
        <div v-for="link in links">
            <li><a v-bind:href="link.url">{{ link.text }}</a></li>
        </div>
        <!-- {{ scrollY }} -->
      </ul>
    </div>
  </nav>
</template>



<script>
// Component def
export default {
  // Local state
  data: () => ({
    links: [
      { text: 'Our Story', url: 'https://medium.com/@amityapp/introducing-amity-b6f2f244c52f' },
      { text: 'Press', url: 'https://medium.com/@amityapp/amity-a-messaging-experience-with-a-new-level-of-live-interaction-media-kit-a894e1175c77' },
      { text: 'Contact', url: 'mailto:hello@amity.io' }
    ],
    scrollY: 0,
    window: window,
    htmlHeight: Math.max(document.documentElement.clientHeight, document.body.scrollHeight),
  }),
  methods: {
    handleScroll () {
      this.scrollY = window.scrollY
    },
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
@media screen and (min-aspect-ratio: 8/16) and (max-width: 600px) {
  .nav-bar {
    height: 30px;
  }
}

@media screen and (min-aspect-ratio: 16/10) and (max-width: 780px) {
  .nav-bar {
    height: 30px;
  }
}

.hide-nav {
  position: fixed;
  opacity: 0;
  transition: all 0.4s ease;
}

.nav-bar {
  position: fixed;
  top: 0;
  right: 0;
  opacity: 1;
  transition: all 0.4s ease;
  background-color: rgba(0,0,0,0.8);
  width: 100vw;
  height: 50px;
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  z-index: 3;
}

.nav-inside {
  height: 0vh;
  width: 300px;
  margin-right: 2%;

  ul {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin-top: 5%;

    li {
      font-size: 0.8em;
      a {
        color: #ddd;
        transition: color 0.2s ease;
      }
      a:hover {
        color: #E0C082;
        transition: color 0.2s ease;
      }
    }
  }
}
</style>

