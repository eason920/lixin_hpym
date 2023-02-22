<template>
  <div class="relative">
    <section id="sec0">
      <div class="title"
        data-aos-once="false"
        data-aos="fade-in"
        data-aos-delay="0"
        data-aos-duration="800"
      >
        <img src="./S0/title.png" />
      </div>
      <div class="box">
        <swiper :options="swiperOptions">
          <swiper-slide v-for="(item, i) in swipList" :key="'box' + i">
            <div target="news" class="box_item">
              <div class="box_mask"></div>
              <div class="box_from">{{ item.from }}</div>
              <div class="box_text"><span>{{ item.msg }}</span></div>
              <div class="box_read">READ NEWS</div>
              <a :href="item.link" target="_blank" class="box_link"></a>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </section>
  </div>
</template>

<style lang="sass" scoped>
@import src/assets/style/myvar
@import ./sass/share
// 圖片
@media screen and (min-width: $bp-pc)
  .swiper-slide
    background:
      position: center
      size: cover
    &:nth-child(1), &:nth-child(8), &:nth-child(15)
      background-image: url('./S0/1.png')

    &:nth-child(2), &:nth-child(9), &:nth-child(16)
      background-image: url('./S0/2.png')

    &:nth-child(3), &:nth-child(10), &:nth-child(17)
      background-image: url('./S0/3.png')

    &:nth-child(4), &:nth-child(11), &:nth-child(18)
      background-image: url('./S0/4.png')
    &:nth-child(5), &:nth-child(12), &:nth-child(19)
      background-image: url('./S0/5.png')
    &:nth-child(6), &:nth-child(13), &:nth-child(20)
      background-image: url('./S0/6.png')
    &:nth-child(7), &:nth-child(14), &:nth-child(21)
      background-image: url('./S0/7.png')

@media screen and (max-width: $bp-mb)

  .swiper-slide
    background:
      position: center
      size: cover
    &:nth-child(1), &:nth-child(8), &:nth-child(15)
      background-image: url('./S0/3.png')

    &:nth-child(2), &:nth-child(9), &:nth-child(16)
      background-image: url('./S0/4.png')

    &:nth-child(3), &:nth-child(10), &:nth-child(17)
      background-image: url('./S0/5.png')

    &:nth-child(4), &:nth-child(11), &:nth-child(18)
      background-image: url('./S0/6.png')
    &:nth-child(5), &:nth-child(12), &:nth-child(19)
      background-image: url('./S0/7.png')
    &:nth-child(6), &:nth-child(13), &:nth-child(20)
      background-image: url('./S0/1.png')
    &:nth-child(7), &:nth-child(14), &:nth-child(21)
      background-image: url('./S0/2.png')

// 總高
@media screen and (min-width: $bp-pc)
  .swiper-container, // height 1
  .swiper-wrapper,
  .swiper-slide,
  .box_item
    height: 20vw
    // max-height: 70vh
@media screen and (max-width: $bp-mb) and (orientation: portrait)
  .swiper-container,
  .swiper-wrapper,
  .swiper-slide,
  .box_item
    height: 50vw

@media screen and (max-width: $bp-mb) and (orientation: landscape)
  .swiper-container,
  .swiper-wrapper,
  .swiper-slide,
  .box_item
    height: 100vh

// --------------------------------
// -- 我內部介面
// --------------------------------
#sec0
  position: relative
  z-index: 10
  display: flex
  flex-direction: column

%masker
  position: absolute
  top: 0
  right: 0
  bottom: 0
  left: 0
  margin: auto
.box

.box_item
  position: relative

.box_mask
  @extend %masker
  background-color: #000
  opacity: .5
.box_from
  position: absolute
  top: 15px
  left: 18px
  font:
    size: 12px
    weight: ligther
    family: "Noto Sans TC" !important
  letter-spacing: 1px
  color: #9FD9F6
.box_text
  bottom: 30px
  position: absolute
  width: 90%
  left: 5%
  color: #fff
  background: rgba(1,17,28,.8)
  display: flex
  align-items: center
  justify-content: center
  padding: 8px 10px
  span
    font:
      size: 13px
      family: "Noto Sans TC" !important
      weight: lighter
    line-height: 1.4
    letter-spacing: 1px
    display: -webkit-box
    -webkit-line-clamp: 2
    -webkit-box-orient: vertical
    overflow: hidden
.box_read
  color: #9FD9F6
  font:
    size: 12px
    weight: bold
    family: "Noto Sans TC" !important
  text-decoration: none
  position: absolute
  bottom: 8px
  right: 6%
  text-shadow: black 0 0 5px, black 0 0 5px, black 0 0 5px
.box_link
  @extend %masker
@media screen and (min-width: $bp-pc)
  #sec0

  .box
    margin:
      left: 10vw
      bottom: 11vw
    width: 90vw
  .box_item:hover
    .box_mask
      transition: .3s
      opacity: 0
  .box_mask
    // @extend %masker
  .box_text
    // height: 36px
  .box_link
    top: 18vw

@media screen and (max-width: $bp-mb)
  .box
    width: 120vw
    margin:
      left: -2vw
    order: 2
  .title
    order: 1
  .box_text
    // height: 22px

// --------------------------------
// --title
// --------------------------------
.title
  margin: 0 auto
  img
    width: 100%

@media screen and (min-width: $bp-pc)
  .title
    width: 41vw
    margin:
      bottom: 3vw
@media screen and (max-width: $bp-mb)
  .title
    width: 80vw
    margin:
      top: 18vw
      bottom: 5vw

</style>

<script>
import { isMobile, isTablet } from '@/utils'
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

export default {
  name: 'section1',

  components: {
    Swiper,
    SwiperSlide
  },

  data() {
    return {
      isMobile,
      isTablet,
      bIsOpen: false,
      swipList: [
        {from: '#ETToday房產1', msg: '「1北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/1'},
        {from: '#ETToday房產2', msg: '「2北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/2'},
        {from: '#ETToday房產3', msg: '「3北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/3'},
        {from: '#ETToday房產4', msg: '「4北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/4'},
        {from: '#ETToday房產5', msg: '「5北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/5'},
        {from: '#ETToday房產6', msg: '6「北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/6'},
        {from: '#ETToday房產7', msg: '7「北士科」台北市最後大型重劃區明眼人的價值出手的明的價值出手的價值出手！「北士科」台北市最後大型重劃區', link: 'https://hahow.in/7'}
      ],
      swiperOptions: {
        breakpoints: {
          // when window width is >= 320px
          768: {
            slidesPerView: 4.5,
            spaceBetween: 15
          },
          // when window width is >= 640px
          0: {
            slidesPerView: 2.3,
            spaceBetween: 10
          }
        },
        // slidesPerView: 4.5,
        // spaceBetween: 15,
        loop: true, // 是否 slide 後循環
        // initialSlide: 0, // 最初 pic index
        // slidesPerView: 'auto',
        autoplay: {
          delay: 1500,
          disableOnInteraction: false // 換頁後是否停止 autoplay
        },
        speed: 1600,
        grabCursor: true,
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
          type: 'bullets'
        },
      }
    }
  },

  methods: {},

  created() {},

  mounted() {},

  computed: {}
}
</script>
