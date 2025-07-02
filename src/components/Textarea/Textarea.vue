<script setup lang="ts">
import { ref, defineEmits, nextTick } from "vue";

const text = ref<string>("");

const emit = defineEmits<{
  (evento: "update:text", value: string): void;
}>();

const allowedCharacters = [
  "a",
  "b",
  "c",
  "ç",
  "d",
  "e",
  "f",
  "g",
  "h",
  "i",
  "j",
  "k",
  "l",
  "m",
  "n",
  "o",
  "p",
  "q",
  "r",
  "s",
  "t",
  "u",
  "v",
  "w",
  "x",
  "y",
  "z",
  " ",
];

const emitText = (): void => {
  filterText();

  nextTick(() => {
    emit("update:text", text.value);
  });
};

const filterText = () => {
  const letters = text.value.toLowerCase().split("");
  const filteredText = letters.filter((letter) =>
    allowedCharacters.includes(letter)
  );
  text.value = filteredText.join("");
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
  width: 100%;
  height: 200px;
  resize: none;
  font-size: 1rem;
  font-weight: 400;
  border-radius: 0.25rem;
  padding: 1rem;
}
</style>
