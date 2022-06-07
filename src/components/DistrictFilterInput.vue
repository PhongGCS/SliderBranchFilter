<template>
  <div class="district-filter-input">
        <label for="">Quận / Huyện</label>
        <select @change="onChange">
            <option value="" checked></option>
            <option v-for="(item,index) in listDistrict" :key="index" :value="item"> {{item}} </option>
        </select>
  </div>
</template>

<script>
export default {
  name: 'DistrictFilterInput',
  props: {
    listDistrict: []
  },
  methods: {
    onChange : function(event) {
      let activeDistrict = event.target.value;
      console.log("alo" + activeDistrict);
      this.$emit("emitCurrentActiveDistrict",activeDistrict);
    }
  } 
}
</script>
<style scoped>
  .district-filter-input {
    display: flex;
    flex-direction: column;
  }
</style>
