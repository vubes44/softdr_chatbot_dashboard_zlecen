<template>
  <div id="app">
    <OOrderCard
      :order="{
        name: 'Stworzenie aplikacji webowej',
        company: 'SofTDR',
        date: '2024-06-01',
        email: 'x@gmail.com',
        phone: '123-456-7890',
        status: 'do zrobienia',
      }"
    />
    <OOrderCard
      :order="{
        name: 'Stworzenie aplikacji webowej',
        company: 'SofTDR',
        date: '2024-06-01',
        email: 'x@gmail.com',
        phone: '123-456-7890',
        status: 'do zrobienia',
      }"
    />
  </div>
</template>
<script setup lang="ts">
import OOrderCard from "./components/organisms/OOrderCard.vue";
import MLabelAndValue from "./components/molecules/MLabelAndValue.vue";
</script>
<style lang="scss"></style>
