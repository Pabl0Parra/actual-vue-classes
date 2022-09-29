<template>
  <div id="computed-exercise">
    <h2>
      Directions <br />Generamos dos propiedades de datos reactivos con ref():
      firstName y lastName. Las imprimimos usando moustache syntax, como siempre
      lo hemos hecho. Después generamos una función computada que impirma estas
      dos variables. Creamos dos funciones: una función computada que activa el
      callback de get y set. En el getter apuntas al valor de firstName +
      lastName y en el setter generamos la lógica para aplicar un nuevo valor.
      En la segunda función asignamos un nuevo valor a la variable.
    </h2>
  </div>
  <!--Exercise 1 example without functions -->
  <div id="example-1">
    <h2><strong>Simple example</strong></h2>
    <p>Footballer - {{ firstName }} - {{ lastName }}</p>
    <!-- Exercise 2 -->
    <h2><strong>Computed property function</strong></h2>
    <p>Footballer - {{ favFootballer }}</p>
    <!-- Exercise 3 -->
    <button @click="changeFavFootballer">Change fav footballer</button>
  </div>
</template>

<script setup>
//exercise 1
import { ref, computed } from "vue";
const firstName = ref("Gica");
const lastName = ref("Hagi");

//exercise 2
const favFootballer = computed(() => {
  return `${firstName.value} ${lastName.value}`;
});
//exercise 3
const changeFavFootballer = () => {
  favFootballer2.value = "Leo Messi";
};
const favFootballer2 = computed({
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
]);
</script>

<style scoped>
button {
  border: 1px solid gray;
  padding: 6px;
}
</style>
