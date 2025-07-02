<script setup lang="ts">
import Container from "@/components/Container/Container.vue";
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
      <div class="request">
        <textarea name="text" id="text"></textarea>
      </div>
    </div>
  </Container>
</template>

<style scoped>
h1 {
  font-size: 4rem;
}

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
