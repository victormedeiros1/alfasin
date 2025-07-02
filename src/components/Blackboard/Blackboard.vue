<script setup lang="ts">
import { defineProps } from "vue";

defineProps<{ text: string }>();
</script>

<template>
  <div class="blackboard">
    {{ text }}
  </div>
</template>

<style scoped></style>
