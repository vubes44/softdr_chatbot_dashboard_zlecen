<template>
  <div class="p-dashboard">
    <ALabel componentType="h2" styleType="apptitle" margin="0 0 1rem 0"
      >Dashboard zleceń</ALabel
    >
    <OOrderList :listTitle="'Nowe'" :orderList="newOrders" />
    <OOrderList :listTitle="'W trakcie'" :orderList="inProgressOrders" />
    <OOrderList :listTitle="'Zakończone'" :orderList="completedOrders" />
  </div>
</template>
<script setup lang="ts">
import ALabel from "../atoms/ALabel.vue";
import OOrderList from "../organisms/OOrderList.vue";
import type { Order } from "../../types/types";

// Example orders to demonstrate lists in the dashboard.
// These are simple, static examples; replace with real data or API calls as needed.
const newOrders: Order[] = [
  {
    name: "Plakat reklamowy",
    customer: "Firma X",
    sendDate: "2026-03-20",
    deadline: "2026-04-05",
    email: "kontakt@firma-x.pl",
    phone: "+48 600 000 001",
    description: "Druk plakatów A2, 100 szt. - projekt w załączniku",
  },
  {
    name: "Ulotki eventowe",
    customer: "Agencja Y",
    sendDate: "2026-03-28",
    deadline: "2026-04-10",
    email: "biuro@agencja-y.pl",
    phone: "+48 600 000 002",
    description: "Ulotki DL, dwustronne, papier kreda 150g",
  },
];

const inProgressOrders: Order[] = [
  {
    name: "Katalog produktowy",
    customer: "Sklep Z",
    sendDate: "2026-02-15",
    deadline: "2026-03-30",
    email: "zamowienia@sklep-z.pl",
    phone: "+48 600 000 003",
    description: "Projekt katalogu 24 str., format A4",
  },
];

const completedOrders: Order[] = [
  {
    name: "Baner na stronę",
    customer: "Startup A",
    sendDate: "2026-01-10",
    deadline: "2026-01-15",
    email: "hello@startupa.com",
    phone: "+48 600 000 004",
    description: "Baner hero + wersje responsywne",
  },
  {
    name: "E-mail marketing",
    customer: "Klient B",
    sendDate: "2026-02-01",
    deadline: "2026-02-05",
    email: "kontakt@klient-b.pl",
    phone: "+48 600 000 005",
    description: "Kampania 3 wiadomości, segmentacja klientów",
  },
];
</script>
<style scoped lang="scss"></style>
