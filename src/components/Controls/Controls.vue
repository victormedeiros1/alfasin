<script setup lang="ts">
import { ref, defineEmits, nextTick } from "vue";

const toggleCharacters = ref<boolean>(false);

const emit = defineEmits<{
  (evento: "update:toggleCharacters", value: string): void;
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
  </div>
</template>

<style scoped>
.controls {
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
input:hover,
label:hover {
  cursor: pointer;
}
</style>
