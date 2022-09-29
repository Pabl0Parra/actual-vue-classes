<template>
  <div>
    <MyBioName :name="name" />
    <MyBioAge :age="age" />
    <MyBioBirthplace :birthplace="birthplace" />
    <MyBioCurrentLocation :currentLocation="currentLocation" />
  </div>
</template>

<script setup>
import MyBioName from "./MyBioName.vue";
import MyBioAge from "./MyBioAge.vue";
import MyBioBirthplace from "./MyBioBirthplace.vue";
import MyBioCurrentLocation from "./MyBioCurrentLocation.vue";
const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  age: {
    type: Number,
  },
  birthplace: {
    type: String,
    default: "Planet Earth",
  },
  currentLocation: {
    type: String,
    default: "Barna",
  },
});
</script>

<style scoped></style>
