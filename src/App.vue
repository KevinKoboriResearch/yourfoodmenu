<template>
  <div id="q-app">
    <router-view />
  </div>
</template>
<script>
export default {
  name: 'App',
  mounted () {
    this.$store.commit('window/updateWindowWidth', window.innerWidth)
    this.$store.commit('window/updateWindowHeight', window.innerHeight)
    this.$nextTick(() => {
      window.addEventListener('resize', this.onResize)
    })
  },
  beforeDestroy () {
    window.removeEventListener('resize', this.onResize)
  },
  methods: {
    onResize () {
      this.$store.commit('window/updateWindowWidth', window.innerWidth)
      this.$store.commit('window/updateWindowHeight', window.innerHeight)
    }
  }
}
</script>

<style>
body::-webkit-scrollbar {
  width: 1em;
}

body::-webkit-scrollbar-thumb {
  background-color: rgb(85, 85, 85);
}

.q-card {
  border-radius: 0px;
}

.img-mini-logo {
  height: 15px;
}

.logo {
  height: 26px;
}

.logo-mini {
  height: 18px;
}

.img-bg {
  height: 100vh;
}

.img-slide {
  height: 50vw;
}

.img-section {
  height: 9vw;
  /* width: 20vw; */
  /* text-align: center; */
  /* width: 50vw; */
  /* height: 680px;
  background: url('./assets/frames/android.png') center top no-repeat;
  background-size: 340px;
  margin: 0 auto 0; */
}

.footer-logo {
  height: 60px;
}

.rotate180 {
  transform: rotate(180deg);
}

.containerSizeTransition {
  transition: width .3s, height .3s;
}
</style>
