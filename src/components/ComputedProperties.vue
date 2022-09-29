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

  <div id="example-2">
    <p>Computed Function Total - {{ total }}</p>
    <!-- adding th () works but it´s not a good way to do it, better the total function -->
    <!-- <p>Regular Function Total - {{ totalRegular() }}</p> -->
  </div>

  <!-- SHOPPING LIST EXAMPLE -->
  <!-- button to add item to list -->
  <div id="example-3">
    <p>
      Computed Functional Total - <strong>{{ total }}</strong>
    </p>
    <button @click="addItem">Add item</button>
  </div>

  <!-- Shopping example with a simple conditional -->
  <h3>Our Shopping List with prices above 200$</h3>
  <div class="shopping" v-for="(item, index) in items" :key="index">
    <div v-if="item.price > 200">
      <ul>
        <li>{{ item.title }} - {{ item.price }}</li>
      </ul>
    </div>
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

// EXAMPLE 2

const items = ref([
  { id: 1, title: "TV", price: 100 },
  { id: 2, title: "Iphone", price: 600 },
  { id: 3, title: "Computer", price: 300 },
  { id: 4, title: "Monitor", price: 700 },
  { id: 5, title: "Mouse", price: 50 },
]);
// Regular function
// const totalRegular = () => {
//   console.log("Total executed normally[]");
//   return items.value.reduce((total, curr) => (total += curr.price), 0);
// };

// Computed function
const total = computed(() => {
  console.log("Total computed via Computed Property");
  return items.value.reduce((total, curr) => (total += curr.price), 0);
});

// function to addItem to list
const addItem = () => {
  items.value.push({ id: 7, title: "Headphones", price: 80 });
};

//Computed Function to conditionally rendering items who are more expensive than 200
const expensiveItems = computed(() => {
  return items.value.filter((item) => item.price > 200);
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
  font-size: 24px;
}

a {
  color: #42b983;
}
p {
  font-size: 2rem;
}
.shopping {
  padding: 0 2rem;
  border: 1px black solid;
}
button {
  margin: 10px 0;
  border: 1px solid;
  padding: 10px;
}
</style>
