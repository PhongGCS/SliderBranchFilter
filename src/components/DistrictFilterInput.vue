<template>
  <div class="district-filter-input cs_custom_select">
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
