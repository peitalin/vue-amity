
<template>
  <div class='nav-bar'>
    <div class='nav-inside'>
      <ul>
        <div v-for="link in links">
            <li><a v-bind:href="link.url">{{ link.text }}</a></li>
        </div>
      </ul>
    </div>
  </div>
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
    ]
  }),
  methods: {
    reverseMessage: function() {
      this.message = this.message.split('').reverse().join('')
    }
  }
}
</script>


<style lang='sass'>

.nav-bar {
  background-color: rgba(0,0,0,0);
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  z-index: 1;
}
.nav-inside {
  height: 0vh;
  width: 300px;
  ul {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    li {
      font-size: 0.8em;
      color: #aaa;
    }
  }
}
</style>

