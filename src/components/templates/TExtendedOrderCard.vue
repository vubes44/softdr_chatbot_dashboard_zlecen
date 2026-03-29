<template>
  <transition name="modal-fade">
    <div
      v-if="props.show"
      class="t-extended-order-card"
      @keydown.esc="handleEsc"
    >
      <div class="overlay" @click.self="close">
        <div
          class="modal"
          role="dialog"
          aria-modal="true"
          aria-label="Order details"
        >
          <header class="modal__header">
            <ALabel
              componentType="h5"
              styleType="apptitle"
              :margin="'0 0 0.5rem 0'"
              >Szczególy zlecenia</ALabel
            >
          </header>

          <section class="modal__body">
            <MLabelAndValue
              label="Nazwa zlecenia"
              :value="props.order.name"
              totalMargin="0.25rem 0"
            />
            <MLabelAndValue
              label="Klient"
              :value="props.order.customer"
              totalMargin="0.25rem 0"
            />
            <MLabelAndValue
              label="Data na wykonanie"
              :value="props.order.date"
              totalMargin="0.25rem 0"
            />
            <MLabelAndValue
              label="Email"
              :value="props.order.email"
              totalMargin="0.25rem 0"
            />
            <MLabelAndValue
              label="Nr. tel."
              :value="props.order.phone"
              totalMargin="0.25rem 0"
            />

            <div class="m-description" style="margin-top: 0.75rem">
              <ALabel
                componentType="label"
                styleType="secondary"
                :margin="'0 0 0.25rem 0'"
                >Opis</ALabel
              >
              <ALabel componentType="p" :margin="'0'">{{
                props.order.description || "-"
              }}</ALabel>
            </div>
          </section>

          <footer class="modal__footer">
            <AButton type="submit" @click="onEdit">Edytuj</AButton>
            <AButton @click="close">Zamknij</AButton>
          </footer>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup lang="ts">
import type { Order } from "../../types/types";
import ALabel from "../atoms/ALabel.vue";
import AButton from "../atoms/AButton.vue";
import MLabelAndValue from "../molecules/MLabelAndValue.vue";

const props = withDefaults(
  defineProps<{
    order: Order;
    show?: boolean;
  }>(),
  {
    show: false,
  },
);

const emit = defineEmits<{
  (e: "close"): void;
  (e: "edit"): void;
}>();

const close = () => emit("close");
const onEdit = () => emit("edit");

const handleEsc = (e: KeyboardEvent) => {
  if ((e as any).key === "Escape" || (e as any).key === "Esc") close();
};
</script>

<style scoped lang="scss">
.t-extended-order-card {
  .overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;

    .modal {
      background: #1f1f1f;
      color: #eee;
      width: min(720px, 95%);
      max-height: 90vh;
      overflow: auto;
      border-radius: 8px;
      padding: 1rem;
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.6);
      display: flex;
      flex-direction: column;
      gap: 0.75rem;

      &__header,
      &__footer {
        display: flex;
        align-items: center;
        justify-content: space-between;
      }

      &__body {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
      }
    }
  }
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.18s ease;
}
.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}
</style>
