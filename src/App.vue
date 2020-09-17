<template>
  <div id="q-app">
    <!-- <h1 class="bg-green"><br><br><br><br><br>{{v1}}</h1> -->
    <router-view />
  </div>
</template>
<script>
export default {
  data () {
    return {
      // v1: null,
      // v2: null
    }
  },
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
      // this.width(window.innerWidth)
      // this.height(window.innerHeight)
      this.$store.commit('window/updateWindowWidth', window.innerWidth)
      this.$store.commit('window/updateWindowHeight', window.innerHeight)
    }
  }
  // watch: {
  //   width: {
  //     get () {
  //       return this.v1
  //     },
  //     set (val) {
  //       this.v1 = val
  //       this.$store.commit('window/updateWindowWidth', val)
  //     }
  //   },
  //   height: {
  //     get () {
  //       return this.v2
  //     },
  //     set (val) {
  //       this.v2 = val
  //       this.$store.commit('window/updateWindowHeight', val)
  //     }
  //   }
  // }
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
  height: 16px;
}

.logo-mini {
  height: 18px;
}

.img-bg {
  height: 100vh;
}

.img-slide {
  /* height: 300px; */
  height: 50vw;
}

.img-slide-cardapio {
  /* height: 200px; */
  height: 30vw;
}
.img-section {
  height: 200px;
  /* height: 11vw; */
}

.footer-logo {
  height: 60px;
}

.rotate180 {
  transform: rotate(180deg);
}

.containerSizeTransition {
  transition: width 0.3s, height 0.3s;
}

.selectDisable {
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -o-user-select: none;
  user-select: none;
}
</style>
