<script setup>
import MyBio from "./components/MyBio.vue";
import TwoWayBinding from "./components/TwoWayBindin/TwoWayBinding.vue";
import ComputedProperties from "./components/ComputedProperties.vue";
import ComputedExercise from "./components/ComputedExercise.vue";
import Watchers from "./components/Watchers.vue";
import WatchersExercise from "./components/WatchersExercise.vue";
</script>

<template>
  <!-- <div>
    <h1 className="text-3xl underline">Hello world!</h1>
    <MyBio
      name="Pablo Parra"
      age="42"
      birthplace="Granada"
      currentLocation="Barcelona"
    />
  </div>
  <TwoWayBinding /> -->
  <!-- <ComputedProperties /> -->
  <!-- <ComputedExercise /> -->
  <Watchers />
  <WatchersExercise />
</template>

<style scoped>
* {
  margin: 10px 0;
}
</style>
