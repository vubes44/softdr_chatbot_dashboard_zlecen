<template>
  <div id="app">
    <OOrderList listTitle="Zlecenia" :orderList="orders" />

    <!-- Button to open the modal for testing -->
    <div style="margin-top: 20px">
      <AButton @click="openTestModal">Otwórz przykładowe zlecenie</AButton>
    </div>

    <!-- Modal component (overlay) -->
    <TExtendedOrderCard
      :order="selectedOrder"
      :show="isModalOpen"
      @close="isModalOpen = false"
      @edit="handleEdit"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import OOrderList from "./components/organisms/OOrderList.vue";
import AButton from "./components/atoms/AButton.vue";
import TExtendedOrderCard from "./components/templates/TExtendedOrderCard.vue";
import type { Order } from "./types/types";

// existing list (you already have this in your App.vue)
const orders: Order[] = [
  {
    name: "Stworzenie aplikacji webowej",
    customer: "SofTDR",
    sendDate: "2026-03-28",
    deadline: "2026-05-05",
    email: "kontakt@firmaa.pl",
    phone: "+48 123 456 789",
    description: "Opis zlecenia 001",
  },
  // ... other orders
];

const isModalOpen = ref(false);

// start with the first order for quick testing; you can set this from a row click later
const selectedOrder = ref<Order>(orders[0]);

function openTestModal() {
  selectedOrder.value = orders[0]; // or set to any order
  isModalOpen.value = true;
}

function handleEdit() {
  // called when the modal emits "edit"
  console.log("Edit requested for", selectedOrder.value);
  isModalOpen.value = false;
  // TODO: route to edit page or show edit form
}
</script>

<style lang="scss">
#app {
  padding: 20px;
}
</style>
