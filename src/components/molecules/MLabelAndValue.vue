<template>
  <div
    class="m-label-and-value"
    :class="{ 'm-label-and-value--vertical': props.layout === 'vertical' }"
    :style="{ margin: props.totalMargin }"
  >
    <ALabel
      :componentType="labelComponentType"
      :styleType="labelStyleType"
      :margin="labelMargin"
    >
      {{ label }}
    </ALabel>

    <ALabel
      :componentType="valueComponentType"
      :styleType="valueStyleType"
      :margin="valueMargin"
    >
      {{ value }}
    </ALabel>
  </div>
</template>
<script setup lang="ts">
import { computed } from "vue";
import ALabel from "../atoms/ALabel.vue";

const props = withDefaults(
  defineProps<{
    layout?: "horizontal" | "vertical";
    label?: string;
    value?: string;
    labelComponentType?:
      | "h1"
      | "h2"
      | "h3"
      | "h4"
      | "h5"
      | "p"
      | "label"
      | "span";
    valueComponentType?:
      | "h1"
      | "h2"
      | "h3"
      | "h4"
      | "h5"
      | "p"
      | "label"
      | "span";
    boldLabelOrValue?: "none" | "label" | "value" | "label value";
    labelMargin?: string;
    valueMargin?: string;
    totalMargin?: string;
  }>(),
  {
    layout: "horizontal",
    label: "",
    value: "",
    labelComponentType: "label",
    valueComponentType: "label",
    boldLabelOrValue: "none",
    labelMargin: "0",
    valueMargin: "0",
    totalMargin: "0",
  },
);

const labelStyleType = computed(() =>
  (props.boldLabelOrValue ?? "").includes("label")
    ? "textlabel_bold"
    : "textlabel",
);

const valueStyleType = computed(() =>
  (props.boldLabelOrValue ?? "").includes("value")
    ? "textlabel_bold"
    : "default",
);
</script>
<style lang="scss">
.m-label-and-value {
  display: flex;
  margin: var(--total-margin, 0);
  gap: 0.25rem;
}

.m-label-and-value--vertical {
  flex-direction: column;
  align-items: flex-start;
}
</style>
