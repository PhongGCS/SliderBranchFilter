<template>
  <div class="store-location-map" v-if="activeBranch">
    <h3>{{activeBranch.name}}</h3>
    <div class="cs_phone_and_location">
        <ul>
            <li>{{activeBranch.address}}</li>
            <li>{{activeBranch.phone}}</li>
        </ul>
        <a :href="activeBranch.map" class="cs_btn">Xem trên Google Map</a>
    </div>
  </div>
</template>
<script>
export default {
  name: 'StoreLocationMap',
  props: {
    activeBranch: Object
  },
  methods: {

  }
}
</script>

<style>
.cs_phone_and_location {
    display: flex;
    justify-content: space-between;
}
.cs_btn {
  padding: 10px 20px;
  border: solid 1px #ededed;
  border-radius: 5px;
}
</style>