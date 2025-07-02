<script setup lang="ts">
import { ref } from "vue";
import Container from "@/components/Container/Container.vue";
import Textarea from "@/components/Textarea/Textarea.vue";
import Blackboard from "@/components/Blackboard/Blackboard.vue";
import Controls from "@/components/Controls/Controls.vue";

const text = ref<string>("");
const toggleCharacters = ref<boolean>(false);
</script>

<template>
  <Container>
    <div class="header">
      <h1 class="header__title">ALFASIN</h1>
      <p class="header__description">
        Bem-vindo ao Alfasin, um conversor de alfabeto escrito para alfabeto de
        libras
      </p>
      <div class="header__controls">
        <Controls v-model:toggleCharacters="toggleCharacters" />
      </div>
    </div>
    <div class="content">
      <Textarea v-model:text="text" />
      <Blackboard :text="text" :toggleCharacters="toggleCharacters" />
    </div>
  </Container>
</template>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.header__title {
  font-size: 4rem;
}
.header__description {
  font-size: 1.25rem;
  margin: -1rem 0 1rem 0;
}
.header__controls {
  width: 100%;
}
.content {
  width: 100%;
  max-width: 1000px;
}
</style>
