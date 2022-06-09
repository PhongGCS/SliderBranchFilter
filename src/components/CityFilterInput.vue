<template>
  <div class="city-filter-input cs_custom_select">
        <label for="">Tỉnh/Thành phố</label>
        <select @change="onChange">
            <option v-for="(item,index) in listCity" :key="index" :value="item"> {{item}} </option>
        </select>
  </div>
</template>

<script>
export default {
  name: 'CityFilterInput',
  props: {
    listCity: []
  },
  methods: {
    onChange : function(event) {
      let activeCity = event.target.value;
      this.$emit("emitCurrentActiveCity",activeCity);
    }
  }
}
</script>

<style>
  .city-filter-input {
    display: flex;
    flex-direction: column;
  }
</style>