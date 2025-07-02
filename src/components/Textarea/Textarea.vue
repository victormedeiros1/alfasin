<script setup lang="ts">
import { ref, watch, defineEmits, nextTick } from "vue";

const text = ref<string>("");

const emit = defineEmits<{
  (evento: "update:text", value: string): void;
}>();

const emitText = (): void => {
  nextTick(() => {
    emit("update:text", text.value);
  });
};
</script>

<template>
  <div class="textearea">
    <textarea
      v-model="text"
      name="text"
      id="text"
      @update:model-value="emitText"
    />
  </div>
</template>

<style scoped>
textarea {
  width: 600px;
  height: 200px;
  resize: none;
  font-size: 1rem;
  font-weight: 400;
  border-radius: 0.25rem;
  padding: 1rem;
}
</style>
