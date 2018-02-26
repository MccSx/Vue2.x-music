<template>
  <div class="swiper-container">
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="item in recommends" :key="item.id">
        <a :href="item.linkUrl">
          <img :src="item.picUrl">
        </a>
      </div>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper from 'swiper'
import 'swiper/dist/css/swiper.min.css'

export default {
  props: ['recommends'],
  mounted () {
    this.mySwiper = new Swiper('.swiper-container', {
      loop: true,
      autoplay: {
        delay: 1000,
        disableOnInteraction: false
      },
      pagination: {
        el: '.swiper-pagination',
        type: 'custom',
        renderCustom: function (swiper, current, total) {
          const activeColor = '#ffcd32'
          const activeWidth = '20px'
          const activeRadius = '5px'
          const normalColor = '#aeaeae'
          const nomalWidth = '8px'
          const nomalRadius = '50%'
          let color = ''
          let width = ''
          let radius = ''
          let paginationStyle = ''
          let html = ''
          for (let i = 1; i <= total; i++) {
            if (i === current) {
              color = activeColor
              width = activeWidth
              radius = activeRadius
            } else {
              color = normalColor
              width = nomalWidth
              radius = nomalRadius
            }
            paginationStyle = `background:${color};opacity:0.8;width:${width};height:8px;border-radius:${radius};margin-right:0.875rem;display:inline-block;`
            html += `<span class="swiper-pagination-bullet" style=${paginationStyle}></span>`
          }
          return html
        }
      }
    })
  },
  activated () {
    this.mySwiper.autoplay.start()
  },
  deactivated () {
    this.mySwiper.autoplay.stop()
  }
}
</script>

<style lang="stylus" scoped rel="stylesheet/stylus">
.swiper-container
  width : 100%
  height : 10rem
  .swiper-wrapper
    width : 100%
    height : 100%
    .swiper-slide
      background-position: center
      background-size: cover
      width : 100%
      height : 100%
      img
        width : 100%
        height : 100%
</style>