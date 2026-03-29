<template>
  <div class="o-order">
    <ALabel componentType="h2" margin="0 0 10px 0">
      {{ props.order.name }}
    </ALabel>
    <ALabel componentType="h3" margin="0 0 20px 0">
      {{ props.order.customer }}
    </ALabel>
    <MLabelAndValue
      layout="vertical"
      :label="'Data wysłania'"
      labelComponentType="h3"
      :value="props.order.sendDate"
      totalMargin="10px 0"
    />
    <MLabelAndValue
      layout="vertical"
      :label="'Na kiedy'"
      labelComponentType="h3"
      :value="props.order.deadline"
      totalMargin="10px 0"
    />
    <MLabelAndValue
      layout="vertical"
      :label="'Email'"
      labelComponentType="h3"
      :value="props.order.email"
      totalMargin="10px 0"
    />
    <MLabelAndValue
      layout="vertical"
      :label="'Nr. tel.'"
      labelComponentType="h3"
      :value="props.order.phone"
      totalMargin="10px 0"
    />
    <AButton @click="showDetails()">Szczegóły zlecenia</AButton>
  </div>
</template>
<script setup lang="ts">
import MLabelAndValue from "../molecules/MLabelAndValue.vue";
import ALabel from "../atoms/ALabel.vue";
import AButton from "../atoms/AButton.vue";
import type { Order } from "../../types/types";

const props = defineProps<{
  order: Order;
}>();

const showDetails = () => {};
</script>
<style lang="scss">
.o-order {
  background-color: rgb(50, 50, 50);
  border-radius: 10px;
  padding: 20px;
  width: 400px;
  text-align: left;
  margin-bottom: 10px;
}
</style>
