<template>
  <button
    class="a-button"
    :class="{
      'a-button--disabled': props.isDisabled || props.isLoading,
      'a-button--account-option': props.type === 'account-option',
      'a-button--submit': props.type === 'submit',
      'a-button--another': props.type === 'another',
    }"
    :disabled="props.isDisabled || props.isLoading"
    @click="handleClick"
  >
    <template v-if="isLoading">
      <span class="a-button__loader" />
    </template>
    <template v-else>
      <slot />
    </template>
  </button>
</template>
<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    isLoading?: boolean;
    isDisabled?: boolean;
    type?: "account-option" | "submit" | "another";
  }>(),
  {
    isDisabled: false,
    isLoading: false,
    type: "another",
  },
);

const emit = defineEmits<{
  (e: "click", event: MouseEvent): void;
}>();

const handleClick = (event: MouseEvent) => {
  if (props.isDisabled || props.isLoading) return;
  emit("click", event);
};
</script>
<style lang="scss">
.a-button {
  border: none;
  font-family: calibri;
  transition: 0.3s;

  &:not(.a-button--disabled):hover {
    background-color: rgb(40, 40, 40);
    color: white;
    border: 1px solid white;
  }

  &--disabled {
    cursor: auto;
    opacity: 0.5;
  }

  &--account-option {
    background-color: #ffffff;
    color: #3b3b3b;
    width: 200px;
  }
  &--submit {
    background-color: rgb(100, 100, 200);
    color: rgb(240, 240, 241);
  }
  &--another {
    background-color: rgb(80, 35, 184);
    color: white;
    border-radius: 2px;
  }
  &__loader {
    width: 16px;
    height: 16px;
    border: 2px solid #f3f3f3;
    border-top: 2px solid #555;
    border-radius: 50%;
    animation: rotate 1s linear infinite;
  }
  @keyframes rotate {
    to {
      transform: rotate(360deg);
    }
  }
}
</style>
