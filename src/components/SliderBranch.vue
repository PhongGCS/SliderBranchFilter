<template>
  <div class="slider_branch">
    <h3>Hệ thống chi nhánh : {{activeCity}} {{activeDistrict}}</h3>
    {{listImage}}
    <div class="cs-filter-list-branch">
      <CityFilterInput @emitCurrentActiveCity="currentActiveCity" :listCity="listCity"/>
      <DistrictFilterInput @emitCurrentActiveDistrict="currentActiveDistrict" :listDistrict="listDistrict" :key="districtComponentKey" />
    </div>
    <div class="cs-store-location-map">
      <StoreLocationMap :activeBranch="activeBranch" />
    </div>
    <div class="cs-slider-location" >
      <LocationSlider ref="childSliderComponent" @emitCurrentLocationActive="currentLocationActive" :listImage="listImage">

      </LocationSlider>
    </div>
  </div>
</template>

<script>
import CityFilterInput from './CityFilterInput.vue'
import DistrictFilterInput from './DistrictFilterInput.vue'
import StoreLocationMap from './StoreLocationMap.vue'
import LocationSlider from './LocationSlider.vue'
export default {
  name: 'SliderBranch',
  props: {
    msg: String
  },
  data() {
    return {
      listBranchData: [
                  {
                      "city": "HCM",
                      "district": {
                          "Q1": [
                              { 
                                  'id' : '1',
                                  'thumb': "https://picsum.photos/901/400",
                                  'src': "https://picsum.photos/901/400",
                                  'district': "Q1",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'TAKASHIMAYA 1',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                              {
                                  'id' : '2',
                                  'thumb': "https://picsum.photos/903/400",
                                  'src': "https://picsum.photos/903/400",
                                  'district': "Q1",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'CHỢ BẾN THÀNH',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                              {
                                  'id' : '3',
                                  'thumb': "https://picsum.photos/902/400",
                                  'src': "https://picsum.photos/902/400",
                                  'district': "Q1",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'CHỢ BẾN THÀNH 2',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                          ],
                          "Q2": [
                              {
                                  'id' : '4',
                                  'thumb': "https://picsum.photos/905/400",
                                  'src': "https://picsum.photos/905/400",
                                  'district': "Q2",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'VINCOM Q2',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                              {
                                  'id': '900402',
                                  'thumb': "https://picsum.photos/900/402",
                                  'src': "https://picsum.photos/900/402",
                                  'district': "Q2",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'CANTAVIEW Q2',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                          ]
                      }
                  },
                  {
                      "city": "Đồng Nai",
                      "district": {
                          "Biên Hòa 1": [
                              { 
                                  'id' : '1',
                                  'thumb': "https://via.placeholder.com/900x400?text=BIENHOA1_1",
                                  'src': "https://via.placeholder.com/900x400?text=BIENHOA1_1",
                                  'district': "Q1",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'Biên Hòa 1 - BRANCH 1',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                              {
                                  'id' : '2',
                                  'thumb': "https://via.placeholder.com/900x400?text=BIENHOA1_2",
                                  'src': "https://via.placeholder.com/900x400?text=BIENHOA1_2",
                                  'district': "Q1",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'Biên Hòa 1 - BRANCH 2',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                              {
                                  'id' : '3',
                                  'thumb': "https://via.placeholder.com/900x400?text=BIENHOA1_3",
                                  'src': "https://via.placeholder.com/900x400?text=BIENHOA1_3",
                                  'district': "Q1",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'Biên Hòa 1 - BRANCH 3',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                          ],
                          "Biên Hòa 2": [
                              {
                                  'id' : '4',
                                  'thumb': "https://via.placeholder.com/900x400?text=BIENHOA2_1",
                                  'src': "https://via.placeholder.com/900x400?text=BIENHOA2_1",
                                  'district': "Q2",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'Biên Hòa 2 - BRANCH 1',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                              {
                                  'id': '900402',
                                  'thumb': "https://via.placeholder.com/900x400?text=BIENHOA2_2",
                                  'src': "https://via.placeholder.com/900x400?text=BIENHOA2_2",
                                  'district': "Q2",
                                  'city': "HCM",
                                  'map': 'https://goo.gl/maps/5sABbgQN9xJjveHA8',
                                  'name': 'Biên Hòa 2 - BRANCH 2',
                                  'address': '176, đường 20,',
                                  'phone': '0377747747'
                              },
                          ]
                      }
                  }      
              ],
      activeBranch: null,
      listImage: [],
      listCity: [],
      listDistrict: [],
      activeCity: null,
      activeDistrict: null,
      districtComponentKey: 0,
      isFirstInitSlider: true,
    }
  },
  components: {
    CityFilterInput,
    DistrictFilterInput,
    StoreLocationMap,
    LocationSlider
  },
  mounted() {
    this.listCity = this.listBranchData.map(e => {
      return e.city
    });
    
    this.activeCity = this.listBranchData[0].city;
    this.mapListDisctrict()
    console.log(this.listImage)
    this.activeBranch = this.listImage[0];
  },
  methods: {
    currentActiveDistrict: function (activeDistrict) {
      if(activeDistrict) {
        this.activeDistrict = activeDistrict;
        this.mapImageByCityAndDistrict();
      } else {
        return;
      }
    },
    currentLocationActive: function (activeBranch) {
      this.activeBranch = activeBranch;
    },
    currentActiveCity: function (activeCity) {
      this.activeCity = activeCity;
      this.mapListDisctrict();
    },
    mapListDisctrict: function () {
      // Filter to get list disctrit
      let disctrit = this.listBranchData.filter(e => {
          return e.city === this.activeCity;
      }).map(e => {
          return e.district
      });
      this.listDistrict = Object.keys(disctrit[0]);

      //rebuild district component
      this.forceRerender();
      
      // Filter to get list all slide
      this.mapImageByCity(disctrit[0]);
    },
    mapImageByCity: function (disctrits) {
      let lastDisctritsImage = [];
      for (var key in disctrits) {
        let obj = disctrits[key];
        lastDisctritsImage = lastDisctritsImage.concat(obj)
      }
      this.listImage = lastDisctritsImage
      //  rebuild slider
      if(!this.isFirstInitSlider) {
        this.$refs.childSliderComponent.sliderRebuild();
      } else {
        this.isFirstInitSlider = false;
      }
      
    },
    mapImageByCityAndDistrict: function () {
      this.listImage = this.listBranchData.filter(e => {
          return e.city === this.activeCity;
      }).map(e => {
          return e.district[this.activeDistrict]
      })[0];
      
      this.$refs.childSliderComponent.sliderRebuild();
      
      
    },
    forceRerender: function () {
      this.districtComponentKey += 1;  
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.slider_branch {
  max-width: 1000px;
  margin: auto;
  overflow: hidden;
}
.cs-filter-list-branch {
  display: flex;
  justify-content: space-between;
}
</style>
