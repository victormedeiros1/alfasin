<script setup lang="ts">
import { ref, defineEmits, defineProps, nextTick } from "vue";

const props = defineProps<{
  toggleModal: (showModal: boolean) => void;
}>();

const toggleCharacters = ref<boolean>(false);

const emit = defineEmits<{
  (evento: "update:toggleCharacters", value: boolean): void;
  (evento: "update:showModal", value: boolean): void;
}>();

const emitToggleCharacters = (): void => {
  nextTick(() => {
    emit("update:toggleCharacters", toggleCharacters.value);
  });
};
</script>

<template>
  <div class="controls">
    <div class="controls__toggle">
      <input
        type="checkbox"
        id="toggle"
        v-model="toggleCharacters"
        @change="emitToggleCharacters"
      />
      <label for="toggle">Exibir letras</label>
    </div>
    <div class="controls__qrcode">
      <button class="controls__compartilhar" @click="props.toggleModal()">
        QRCode
      </button>
    </div>
  </div>
</template>

<style scoped>
.controls {
  display: flex;
  justify-content: space-between;
  background-color: #fff;
  width: 100%;
  border-radius: 100px;
  border: 1px solid #ccc;
  padding: 0.5rem 1rem;
  margin-bottom: 2rem;
}
.controls__toggle {
  width: fit-content;
  display: flex;
  border-radius: 1rem;
  gap: 0.5rem;
}
.controls__toggle:hover {
  cursor: pointer;
}
.controls__compartilhar {
  background-color: transparent;
  border: none;
  font-size: 1rem;
}
.controls__compartilhar:hover {
  cursor: pointer;
  color: #007bff;
}
input:hover,
label:hover {
  cursor: pointer;
}
</style>
