<script setup lang="ts">
import { ref } from "vue";
import Container from "./components/Container/Container.vue";
import Textarea from "./components/Textarea/Textarea.vue";
import Blackboard from "./components/Blackboard/Blackboard.vue";
import Controls from "./components/Controls/Controls.vue";
import Modal from "./components/Modal/Modal.vue";

const text = ref<string>("");
const toggleCharacters = ref<boolean>(false);
const showModal = ref<boolean>(false);

const toggleModal = () => {
  showModal.value = !showModal.value;
};
</script>

<template>
  <Container>
    <Modal v-if="showModal" :toggleModal="toggleModal" />
    <div class="header">
      <h1 class="header__title">ALFASIN</h1>
      <p class="header__description">
        Bem-vindo ao Alfasin, um conversor de alfabeto escrito para Libras
      </p>
      <div class="header__controls">
        <Controls
          v-model:toggleCharacters="toggleCharacters"
          :toggleModal="toggleModal"
        />
      </div>
    </div>
    <div class="content">
      <Textarea v-model:text="text" />
      <Blackboard :text="text" :toggleCharacters="toggleCharacters" />
    </div>
    <div class="footer">
      <a
        href="https://github.com/victormedeiros1/alfabeto-libras"
        target="_blank"
        >Link do repositório</a
      >
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
  text-align: center;
  margin: -1rem 0 1rem 0;
}
.header__controls {
  width: 100%;
}
.content {
  width: 100%;
  max-width: 1000px;
}
.footer {
  width: 100%;
  height: 4rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border-top: 1px solid #ccc;
  margin-top: auto;
  padding-top: 1rem;
}

a {
  color: #007bff;
  text-decoration: none;
}

@media (max-width: 800px) {
  .header__description {
    font-size: 1rem;
    margin: -1rem 0 1rem 0;
  }

  .footer {
    height: 2rem;
  }
}
</style>
