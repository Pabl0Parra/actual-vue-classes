<template>
  <div id="computed-explanation">
    <h2>
      Explanation<br />Computer properties are something else. dale dur. toma
    </h2>
  </div>
  <div id="example-1">
    <!-- example without functions -->
    <h2>Simple example</h2>
    <p>Guitarrist - {{ firstName }} - {{ lastName }}</p>
    <h2>Simple computed property function</h2>
    <p>Guitarrist - {{ favGuitarrist }}</p>
    <!-- button that changes guitarrist -->
    <button @click="changeFavGuitarrist">Change fav guitarrist</button>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const firstName = ref("Gusavo");
const lastName = ref("Smith");

//Computed property => function
const favGuitarrist = computed(() => {
  return `${firstName.value} ${lastName.value}`;
});
// regular function to trigger computedPropertyFunction and change the name of the guitarrist to something new!
const changeFavGuitarrist = () => {
  favGuitarrist2.value = "Eric Clapton";
};

// We are going to expand the use of a computedProperty by using their respective methods that are associated with such computedProperty, which are getters and setters

const favGuitarrist2 = computed({
  // get() - its monitors for any type of data tha can change
  get() {
    return `${firstName.value} ${lastName.value}`;
  },
  // set() - takes whatever we are monitoring and changes the data for us. We can either write, update, delete
  set(value) {
    const names = value.split(" ");
    firstName.value = names[0];
    lastName.value = names[1];
  },
});
</script>

<style>
h1 {
  font-size: 16px;
}
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
</style>
