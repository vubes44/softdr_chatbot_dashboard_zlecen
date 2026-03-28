<template>
  <div id="app">
    <OOrderCard
      :order="{
        name: 'Stworzenie aplikacji webowej',
        customer: 'SofTDR',
        date: '2024-06-01',
        email: 'x@gmail.com',
        phone: '123-456-7890',
      }"
    />
    <OOrderCard
      :order="{
        name: 'Stworzenie aplikacji webowej',
        customer: 'SofTDR',
        date: '2024-06-01',
        email: 'x@gmail.com',
        phone: '123-456-7890',
      }"
    />
  </div>
</template>
<script setup lang="ts">
import OOrderCard from "./components/organisms/OOrderCard.vue";
</script>
<style lang="scss"></style>
