<template>
  <!-- You can find this swiper instance object in current compomemt by the "mySwiper"  -->
	<div v-swiper:mySwiper="swiperOption">
	  <div class="swiper-wrapper">
	    <div class="swiper-slide" v-for="banner in banners">
	      <img :src="banner">
	    </div>
	  </div>
	  <div class="swiper-pagination swiper-pagination-bullets"></div>
	</div>
</template>

<script>
  export default {
    data () {
      return {
        banners: [
          '/1.jpg',
          '/2.jpg',
          '/3.jpg'
        ],
        swiperOption: {
          autoplay: 5000,
          initialSlide: 1,
          direction : 'horizontal',
          loop: true,
          pagination: '.swiper-pagination',
          paginationElement: 'li',
          onSlideChangeEnd: swiper => {
            console.log('onSlideChangeEnd', swiper.realIndex)
          },
          onTap: swiper => {
            console.log('onTap', swiper.realIndex)
          }
        }
      }
    },
    mounted() {
      console.log('app init', this)
      setTimeout(() => {
        this.banners.push('/5.jpg')
      	console.log('banners update')
      }, 3000)
      console.log(
      	'This is current swiper instance object', this.mySwiper, 
      	'I will slideTo banners 3')
     	this.mySwiper.slideTo(3)
    }
  }
</script>


<style lang="scss" scoped>
  .my-swiper {
    height: 300px;
    width: 100%;

    .swiper-slide {
      text-align: center;
      font-size: 38px;
      font-weight: 700;
      background-color: #eee;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .swiper-pagination {

      > .swiper-pagination-bullet {
        background-color: red;
      }
    }
  }
</style>