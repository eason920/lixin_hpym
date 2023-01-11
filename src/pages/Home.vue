<template>
  <div class="home no-padding-top">
    <Loading :loading="load" />
    <SideNavigation v-if="isSide" />
    <Navigation v-if="!isMobile" />
    <MClose v-else />
    <!-- <Indigator :viewIndex="viewIndex" /> -->
    <!-- <full-page
      ref="fullPage"
      :options="options"
      id="fullpage"
    > -->
    <!-- <vue-lazy-component class="section" id="sectionDe" @init="init">
      <SwiperDemo />
    </vue-lazy-component> -->
    <vue-lazy-component class="section" id="section1" @init="init">
      <S1 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section2" @init="init">
      <img v-if="!isMobile" class="wave wave_l1" src="../projects/hpym/all/wave_l1.png" />
      <S2 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section3" @init="init">
      <img class="wave wave_r1" src="../projects/hpym/all/wave_r1.png" />
      <img v-if="isMobile" class="wave wave_l1" src="../projects/hpym/all/wave_l1.png" />
      <S3 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section4" @init="init">
      <img v-if="!isMobile" class="wave wave_l2" src="../projects/hpym/all/wave_l2.png" />
      <S4 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section5" @init="init">
      <img v-if="!isMobile" class="wave wave_r2" src="../projects/hpym/all/wave_r2.png" />
      <img v-else class="wave wave_l2" src="../projects/hpym/all/wave_l2.png" />
      <S5 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section6" @init="init">
      <img v-if="isMobile" class="wave wave_r1" src="../projects/hpym/all/wave_r1.png" />
      <S6 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section7" @init="init">
      <img v-if="isMobile" class="wave wave_l2" src="../projects/hpym/all/wave_l1.png" />
      <img v-if="isMobile" class="wave wave_r2" src="../projects/hpym/all/wave_r1.png" />
      <S7 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section8" @init="init">
      <S8 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="contact">
      <ContactSection />
    </vue-lazy-component>
    <!-- ======================== -->
    <MobileNav />
  </div>
</template>

<script>
// @ is an alias to /src
import $ from 'jquery'
import Navigation from '@/layouts/Navigation.vue'
import { isMobile } from '@/utils'
import SideNavigation from '@/layouts/SideNavigation.vue'
import ContactSection from '@/layouts/ContactSection.vue'
import MobileNav from '@/layouts/MobileNav.vue'
import Loading from '@/components/Loading.vue'
// import Indigator from '@/components/Indigator.vue'
// import SwiperDemo from '@/projects/hpym/swiperDemo_S7_single.vue'
import MClose from '@/projects/hpym/MClose.vue'
import S1 from '@/projects/hpym/S1.vue'
import S2 from '@/projects/hpym/S2.vue'
import S3 from '@/projects/hpym/S3.vue'
import S4 from '@/projects/hpym/S4.vue'
import S5 from '@/projects/hpym/S5.vue'
import S6 from '@/projects/hpym/S6.vue'
import S7 from '@/projects/hpym/S7.vue'
import S8 from '@/projects/hpym/S8.vue'

export default {
  name: 'home',
  components: {
    Loading,
    // Indigator,
    Navigation,
    SideNavigation,
    ContactSection,
    MobileNav,
    // SwiperDemo,
    MClose,
    S1,
    S2,
    S3,
    S4,
    S5,
    S6,
    S7,
    S8,
  },

  data() {
    return {
      isMobile,
      isSide: false,
      load: true
    }
  },
  created() {
    $(document).ready(() => {
      // Images loaded is zero because we're going to process a new set of images.
      var imagesLoaded = 0
      // Total images is still the total number of <img> elements on the page.
      var totalImages = $('img').length

      const allImagesLoaded = () => {
        this.load = false
      }
      const imageLoaded = () => {
        imagesLoaded++
        if (imagesLoaded === totalImages) {
          allImagesLoaded()
        }
      }
      $('img').each(function(idx, img) {
        $('<img>')
          .on('load', imageLoaded)
          .attr('src', $(img).attr('src'))
      })
    })
  },
  mounted() {
  },
  methods: {
    init() {}
  }
}
</script>

<style lang="sass">
@import "src/assets/style/myvar"
section
// background-color: #000
.wave
  position: absolute
  top: -10vh
.wave_l1, .wave_l2
  left: 0
  width: calc(100 * 100vw / 375)
.wave_r1, .wave_r2
  right: 0
  width: calc(172 * 100vw / 375)
#section8
  background:
    color: #000
@media screen and (min-width: $bp-pc)
  .wave
    top: -10vh
  .wave_l1, .wave_l2
    left: 0
    width: calc(517 * 100vw / 1920)
  .wave_r1, .wave_r2
    right: 0
    width: calc(517 * 100vw / 1920)
  $ga: #141F24
  $gb: #4C7589
  $gc: #649EB9
  $gd: #11556E
  $ge: #00202C
  #section2
    background:
      image: linear-gradient(to bottom, #000, #{$ga})
    z-index: 2
  #section3
    background:
      image: linear-gradient(to bottom, #{$ga}, #{$gb})
    z-index: 3

  #section4
    background:
      image: linear-gradient(to bottom, #{$gb}, #{$gc})
  #section5
    background:
      image: linear-gradient(to bottom, #{$gc}, #{$gd})
  #section6
    background:
      image: linear-gradient(to bottom, #{$gd}, #{$ge})
  #section7
    background:
      image: linear-gradient(to bottom, #{$ge}, #000)
@media screen and (max-width: $bp-mb)
  $ga: #41758A
  $gb: #5A92AC
  $gc: #031217
  $gd: #031217
  #section3
    padding-top: 1px
    background:
      image: linear-gradient(to bottom, #000 30%, #{$ga})
  #section4
    background:
      image: linear-gradient(to bottom, #{$ga}, #{$gb})
  #section5
    background:
      image: linear-gradient(to bottom, #{$gb}, #{$gc})
  #section6
    background:
      image: linear-gradient(to bottom, #{$gc}, #{$gd})
  #section7
    background:
      image: linear-gradient(to bottom, #{$gd}, #000)
</style>

<style lang="sass">
@import url('https://fonts.googleapis.com/css?family=Noto+Serif+TC')
@import "src/assets/style/myvar"
*
  font-family: "Noto Serif TC", serif !important
  letter-spacing: 1px
  // Noto Sans CJK TC  粗細Regular 400
  // Noto Serif CJK TC  粗細Regular 400  Bold 700

section
  overflow: hidden
  position: relative
  // min-height: 30vh

@media screen and (min-width: $bp-pc)
  .wave
    // height:
@media screen and (max-width: $bp-mb)
  .wave
    // height: 43px
</style>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Playball&display=swap');
@import '../assets/style/variableColor.scss';

.section,
.section .fp-slide,
.section .fp-tableCell {
  height: auto !important;
}
</style>
