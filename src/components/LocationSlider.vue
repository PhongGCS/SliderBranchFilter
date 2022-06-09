<template>
  <div class="slider-location-map">
    <div class="big-image" v-if='listImage[currentIndex]'>
        <img :src="listImage[currentIndex].src" alt="">
    </div>
    <div class="wsu-slider">
      <div v-for="(item, index) in listImage" :key="index" @click.prevent="handleSlideChange(index)">
          <img :class="{'active' : currentIndex == index}" :src="item.thumb" id='' alt="">
      </div>
    </div>
    <ul class="controls" id="customize-controls" aria-label="Carousel Navigation" tabindex="0">
          <li class="prev" data-controls="prev" aria-controls="customize" tabindex="-1">
              <i class="fas fa-angle-left fa-5x"></i>
          </li>
          <li class="next" data-controls="next" aria-controls="customize" tabindex="-1">
              <i class="fas fa-angle-right fa-5x"></i>          
          </li>
      </ul>
</div>
</template>
<script>
import { tns } from 'tiny-slider/src/tiny-slider'
export default {
  name: 'StoreLocationMap',
  props: {
    listImage: Array
  },
  data() {
        return {
          currentIndex: 0,
          slider: undefined,
          activeBranch: this.listImage[0]
      }
  },
  mounted() {
    this.slider = tns({
        container: '.wsu-slider',
        items: 6,
        autoplay: true,
        loop: false,
        gutter: 20,
        slideBy: 1,
        mouseDrag: true,
        controlsPosition: "bottom",
        navPosition: "bottom",
        nav: true,
        animateIn: "scale",
        autoplayButtonOutput: false,
        controlsContainer: '#customize-controls',
        controls: false,
        responsive: {
            640: {
                items: 6
            },
            768: {
                items: 6
            },
            900: {
                items: 6
            }
        }
    });


    let customizedFunction = function (info) {
        document.getElementsByClassName(`wsu-${info.index}`);
        //console.log(`${info.index}`);
        // console.log(this.listImage);
        //let info = slider.getInfo(),
       // let indexPrev = info.indexCached;
        let indexCurrent = info.index;
        // info.slideItems.forEach(element => {
        //     element.classList.remove('active');
        // }); 
        for (let item of info.slideItems) {
            item.classList.remove('active');
        }
        info.slideItems[indexCurrent].classList.add('active');
    }

    this.slider.events.on('indexChanged', customizedFunction);
  },
  methods: {
    handleSlideChange(index) {
        if (index !== this.currentIndex){
            setTimeout(() => {
            this.currentIndex = index;
            this.activeBranch = this.listImage[this.currentIndex];
            }, 0);
            this.$emit('emitCurrentLocationActive', this.activeBranch);
        }
    },
    sliderRebuild: function() {
        if (this.slider) {
            console.log("slider rebuild");
            setTimeout(() => {
                this.slider.rebuild();
            }, 0);
            this.currentIndex  = 0;
            
        }
    }
  }
}
</script>

<style lang="scss" scoped>

.slider-location-map .big-image img {
    width: 100%;
    height: 400px;
    object-fit: cover;
}
.wsu-slider img {
    display: inline-block;
    vertical-align: top;
    max-width: 100%;
}

.wsu-slider {
    display: flex;
    position: relative;    
}
.wsu-slider > div {
    width: calc(100% / 6);
}

</style>