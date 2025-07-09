<script setup lang="ts">
import { ref, defineEmits, nextTick } from "vue";

const props = defineProps<{
  toggleModal: (showModal: boolean) => void;
}>();

const emit = defineEmits<{
  (evento: "update:showModal", value: boolean): void;
}>();
</script>
<template>
  <div class="modal">
    <img
      @click="props.toggleModal"
      class="modal__image"
      src="/images/qrcode.png"
    />
  </div>
</template>
<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1000;
}

.modal__image {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: auto;
  border-radius: 10px;
}
</style>
