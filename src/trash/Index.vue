<template>
  <q-page class="flex flex-center">
    <!-- <div>
    <full-page ref="fullpage" :options="options">
      <div class="section">
        <button class="next" @click="$refs.fullpage.api.moveSectionDown()">Next</button>
        <button class="next" @click="$refs.fullpage.api.moveTo(2,2)">2.2</button>
        Section 1
      </div>
      <div class="section">
                <div class="slide">
                    <h3>Slide 2.1</h3>
                </div>
                <div class="slide">
                    <h3>Slide 2.2</h3>
                </div>
                <div class="slide">
                    <h3>Slide 2.3</h3>
                </div>
            </div>
    </full-page>
  </div> -->
  <div>
        <ul id="menu">
            <li data-menuanchor="page1" @click="moveTo(3)" class="active"><a href="#page1">Section 1</a></li>
            <li data-menuanchor="page2" @click="$refs.fullpage.api.setAutoScrolling(false)"><a href="#page2">Section 2</a></li>
            <li data-menuanchor="page3"><a href="#page3">Section 3</a></li>
            <li>
                <a href="https://twitter.com/imac2" target="_blank" rel="noopener" class="twitter-share">
                    <i>
                        <svg viewBox="0 0 512 512">
                            <path d="M419.6 168.6c-11.7 5.2-24.2 8.7-37.4 10.2 13.4-8.1 23.8-20.8 28.6-36 -12.6 7.5-26.5 12.9-41.3 15.8 -11.9-12.6-28.8-20.6-47.5-20.6 -42 0-72.9 39.2-63.4 79.9 -54.1-2.7-102.1-28.6-134.2-68 -17 29.2-8.8 67.5 20.1 86.9 -10.7-0.3-20.7-3.3-29.5-8.1 -0.7 30.2 20.9 58.4 52.2 64.6 -9.2 2.5-19.2 3.1-29.4 1.1 8.3 25.9 32.3 44.7 60.8 45.2 -27.4 21.4-61.8 31-96.4 27 28.8 18.5 63 29.2 99.8 29.2 120.8 0 189.1-102.1 185-193.6C399.9 193.1 410.9 181.7 419.6 168.6z"></path>
                        </svg>
                    </i>
                </a>
            </li>
        </ul>
        <ul class="actions">
            <li>
                <a class="actions-button" href="#" rel="noopener" @click="addSection">Add section</a>
            </li>
            <li>
                <a class="actions-button" href="#" rel="noopener" @click="removeSection">Remove section</a>
            </li>
            <li>
                <a class="actions-button" href="#" rel="noopener" @click="toggleNavigation">Toggle nav</a>
            </li>
            <li>
                <a class="actions-button" href="#" rel="noopener" @click="toggleScrollbar">Toggle scrollBar</a>
            </li>
        </ul>
          <full-page id="fullpage" ref="fullpage" :options="options">
            <div class="section">
                <h3>Section 1</h3>
                <button class="next" @click="$refs.fullpage.api.moveTo(2,2)">2.2</button>
            </div>
            <div class="section">
                <div class="slide">
                    <h3>Slide 2.1</h3>
                </div>
                <div class="slide">
                    <h3>Slide 2.2</h3>
                </div>
                <div class="slide">
                    <h3>Slide 2.3</h3>
                </div>
            </div>
            <div class="section">
                <div class="slide">
                    <h3>Slide 3.1</h3>
                </div>
                <div class="slide">
                    <h3>Slide 3.2</h3>
                </div>
                <div class="slide">
                    <h3>Slide 3.3</h3>
                </div>
            </div>
            <div class="section">
                <div class="slide">
                    <h3>Slide 3.1</h3>
                </div>
                <div class="slide">
                    <h3>Slide 3.2</h3>
                </div>
                <div class="slide">
                    <h3>Slide 3.3</h3>
                </div>
            </div>
            <div class="section">
                <div class="slide">
                    <h3>Slide 2.1</h3>
                </div>
                <div class="slide">
                    <h3>Slide 2.2</h3>
                </div>
                <div class="slide">
                    <h3>Slide 2.3</h3>
                </div>
            </div>
        </full-page>
    </div>
  </q-page>
</template>

<script>
export default {
  // name: 'app',
  data () {
    return {
      options: {
        licenseKey: 'YOUR_KEY_HERE',
        afterLoad: this.afterLoad,
        scrollOverflow: true,
        scrollBar: false,
        // autoScrolling: false,
        menu: '#menu',
        navigation: true,
        anchors: ['page1', 'page2', 'page3', 'page4', 'page5'],
        sectionsColor: ['#41b883', '#ff5f45', '#0798ec', '#fec401', '#1bcee6', '#ee1a59', '#2c3e4f', '#ba5be9', '#b4b8ab']
      }
    }
  },
  // created () {
  //   window.addEventListener('scroll', this.handleScroll)
  // },
  // destroyed () {
  //   window.removeEventListener('scroll', this.handleScroll)
  // },
  // watch: {
  //   handleScroll (event) {
  //     if (window.scrollY > 25) {
  //       this.headerTransition = true
  //     }
  //   }
  // },
  methods: {

    moveTo (val) {
      this.$refs.fullpage.api.moveTo(val)
    },

    afterLoad () {
      console.log('After load')
    },

    addSection (e) {
      e.preventDefault()
      var newSectionNumber = document.querySelectorAll('.fp-section').length + 1

      // creating the section div
      var section = document.createElement('div')
      section.className = 'section'
      section.innerHTML = `<h3>Section ${newSectionNumber}</h3>`

      // adding section
      document.querySelector('#fullpage').appendChild(section)

      // creating the section menu element
      var sectionMenuItem = document.createElement('li')
      sectionMenuItem.setAttribute('data-menuanchor', 'page' + newSectionNumber)
      sectionMenuItem.innerHTML = `<a href="#page${newSectionNumber}">Section${newSectionNumber}</a>`

      // adding it to the sections menu
      var sectionsMenuItems = document.querySelector('#menu')
      sectionsMenuItems.appendChild(sectionMenuItem)

      // adding anchor for the section
      this.options.anchors.push(`page${newSectionNumber}`)

      // we have to call `update` manually as DOM changes won't fire updates
      // requires the use of the attribute ref="fullpage" on the
      // component element, in this case, <full-page>
      // ideally, use an ID element for that element too
      this.$refs.fullpage.build()
    },
    removeSection () {
      var sections = document.querySelector('#fullpage').querySelectorAll('.fp-section')
      var lastSection = sections[sections.length - 1]

      // removing the last section
      lastSection.parentNode.removeChild(lastSection)

      // removing the last anchor
      this.options.anchors.pop()

      // removing the last item on the sections menu
      var sectionsMenuItems = document.querySelectorAll('#menu li')
      var lastItem = sectionsMenuItems[sectionsMenuItems.length - 1]
      lastItem.parentNode.removeChild(lastItem)
    },
    toggleNavigation () {
      this.options.navigation = !this.options.navigation
    },
    toggleScrollbar () {
      console.log('Changing scrollbar...')
      this.options.scrollBar = !this.options.scrollBar
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #ffffff;
}
</style>
