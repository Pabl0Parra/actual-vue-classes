<template>
  <h2>{{ birthplace }}</h2>
</template>

<script setup>
defineProps({
  birthplace: {
    type: String,
    default: "Citizen of the world",
  },
});
</script>

<style></style>
