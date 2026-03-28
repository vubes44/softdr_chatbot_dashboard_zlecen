<template>
  <div class="o-order">
    <ALabel componentType="p" margin="0 5px 0 0">{{
      props.order.status
    }}</ALabel>
    <ALabel componentType="h2" margin="0 0 10px 0">
      {{ props.order.name }}
    </ALabel>
    <ALabel componentType="h3" margin="0 0 20px 0">
      {{ props.order.company }}
    </ALabel>
    <MLabelAndValue
      layout="vertical"
      :label="'Data:'"
      labelComponentType="h3"
      :value="props.order.date"
      totalMargin="10px 0"
    />
    <MLabelAndValue
      layout="vertical"
      :label="'Email:'"
      labelComponentType="h3"
      :value="props.order.email"
      totalMargin="10px 0"
    />
    <MLabelAndValue
      layout="vertical"
      :label="'Nr. tel.:'"
      labelComponentType="h3"
      :value="props.order.phone"
      totalMargin="10px 0"
    />
  </div>
</template>
<script setup lang="ts">
import MLabelAndValue from "../molecules/MLabelAndValue.vue";
import ALabel from "../atoms/ALabel.vue";
type Order = {
  name: string;
  company: string;
  date: string;
  email: string;
  phone: string;
  status: string;
};

const props = defineProps<{
  order: Order;
}>();
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
