<script setup lang="ts">
import { ref } from "vue";
import Container from "@/components/Container/Container.vue";
import Textarea from "@/components/Textarea/Textarea.vue";
import Blackboard from "@/components/Blackboard/Blackboard.vue";

const text = ref<string>("");
</script>

<template>
  <Container>
    <div class="header">
      <div class="header__title">
        <h1>ALFASIN</h1>
      </div>
      <div class="header__controls"></div>
    </div>
    <div class="content">
      <Textarea v-model:text="text" />
      <Blackboard :text="text" />
    </div>
  </Container>
</template>

<style scoped>
h1 {
  font-size: 4rem;
}

.content {
  width: 100%;
  max-width: 1000px;
}
</style>
