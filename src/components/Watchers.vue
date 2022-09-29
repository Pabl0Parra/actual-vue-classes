<template>
  <div id="watcher-explanation">
    <p>
      A watcher is a special Vue.js feature that allows you to spy on one
      property of the component state, and run a function when that property
      value changes.
    </p>
    <p>As the name suggests</p>
  </div>
  <div id="example-1">
    <p>My name is {{ name }}</p>
    <button @click="changeName()">Change my name</button>
  </div>

  <div id="example-2">
    <h3>Volume Tracker (0-20)</h3>
    <p>
      The current volume is <strong>{{ volume }}</strong>
    </p>
    <div>
      <button @click="volume -= 1">Decrease</button>
      <button @click="volume += 1">Increase</button>
    </div>
  </div>

  <div id="example-3">
    <h3>Example 3</h3>
    <button @click="addMovie">Add movie</button>

    <he>Movie List</he>
    <p v-for="(movie, index) in movieList" :key="index">
      {{ movie }}
    </p>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

let name = ref("Flavio");

function changeName() {
  name.value = "Pablo";
}

watch(name, (newValue, oldValue) => {
  console.log(`New value is ${newValue} - the old value was ${oldValue}`);
});

//example 2 - volume tracker
let volume = ref(0);

//Watch function to monitor volme change and display alert msg is user goes over 8 decibels
//Version 1 or long
// watch(volume, (newValue, oldValue) => {
//   if (newValue > oldValue && newValue === 8) {
//     alert(`TURN IT DOWN YOOO`);
//   }
// });
//Version 2 or short , not best use
watch(volume, (newValue, oldValue) => {
  if (newValue === 8) {
    alert(`YOOO TOO LOUDDDDD`);
  }
});
//EXAMPLE 3 - Mutating Arrays
const movieList = ref(["Batman", "Spiderman"]);

function addMovie() {
  movieList.value.push("Saving Private Ryan");
}

watch(
  movieList,
  (newValue, oldValue) => {
    console.log(`Updated List ${newValue}`);
  }
  //   { deep: true }
);
</script>

<style scoped></style>
