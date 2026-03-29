<template>
  <div class="order-list">
    <ALabel componentType="h3" styleType="default" margin="15px 0px">{{
      props.listTitle
    }}</ALabel>
    <template v-if="props.orderList && props.orderList.length">
      <OOrderCard
        v-for="(order, index) in props.orderList"
        :key="index"
        :order="order"
      />
    </template>
    <div v-else class="no-orders">Brak zleceń</div>
  </div>
</template>
<script setup lang="ts">
import ALabel from "../atoms/ALabel.vue";
import OOrderCard from "./OOrderCard.vue";
import type { Order } from "../../types/types";

const props = defineProps<{
  listTitle: String;
  orderList: Order[];
}>();
</script>
<style scoped lang="scss"></style>
