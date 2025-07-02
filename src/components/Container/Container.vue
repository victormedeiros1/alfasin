<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  min-height: 100dvh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem 1.25rem;
}
</style>
