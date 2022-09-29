<template>
  <div id="watcher-explanation">
    <p>
      A watcher is a special Vue.js feature that allows you to spy on one
      property of the component state, and run a function when that property
      value changes.
    </p>
    <p>Do the following exercises:</p>
  </div>
  <div id="example-1">
    <p>My name is {{ name }}</p>
    <button @click="changeName()">Change my name</button>
  </div>
  <div id="exercise-2">
    <h3>Beers Tracker (0-20)</h3>
    <p>
      The current drunkness level is <strong>{{ volume }}</strong>
    </p>
    <div>
      <button @click="volume -= 1">Decrease</button>
      <button @click="volume += 1">Increase</button>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

let name = ref("Maximiliano");

function changeName() {
  name.value = "Pablo";
}

watch(name, (newValue, oldValue) => {
  console.log(`New value is ${newValue} - the old value was ${oldValue}`);
});
</script>

<style>
.watcher-explanation {
  margin-top: 40px;
}
</style>
