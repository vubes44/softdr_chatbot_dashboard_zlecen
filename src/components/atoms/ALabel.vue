<template>
  <component
    :is="props.componentType"
    :class="{
      'a-label--disabled': isDisabled,
      'a-label--apptitle': props.styleType === 'apptitle',
      'a-label--secondary': props.styleType === 'secondary',
    }"
    :style="{ margin: props.margin }"
  >
    <slot />
  </component>
</template>
<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    isDisabled?: boolean;
    componentType?: "h1" | "h2" | "h3" | "h4" | "h5" | "p" | "label" | "span";
    styleType?: "apptitle" | "secondary" | "disabled" | "default";
    margin?: string;
  }>(),
  {
    isDisabled: false,
    componentType: "label",
    styleType: "default",
    margin: "0",
  },
);
</script>
<style scoped lang="scss">
.a-label--disabled {
  color: rgb(202, 202, 202);
  opacity: 0.3;
}
.a-label--apptitle {
  color: rgb(248, 248, 248);
  font-size: 70pt;
  font-family:
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    Roboto,
    Oxygen,
    Ubuntu,
    Cantarell,
    "Open Sans",
    "Helvetica Neue",
    sans-serif;
}
.a-label--secondary {
  color: rgb(200, 200, 200);
  font-family: "calibri";
}
</style>
