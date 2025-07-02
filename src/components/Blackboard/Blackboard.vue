<script setup lang="ts">
import { computed, ref, defineProps } from "vue";
import { signals } from "@/utils";

const props = defineProps<{ text: string }>();
const separateSignals = computed(() => {
  return props.text.split("");
});
</script>

<template>
  <div class="blackboard">
    <div class="blackboard__content">
      <div class="blackboard__signals">
        <div
          class="blackboard__signal-wrapper"
          v-for="(signal, index) in separateSignals"
          :key="index"
        >
          <img
            class="blackboard__signal"
            :src="`/src/assets/images/${signal}.jpg`"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.blackboard__signals {
  display: flex;
  align-items: baseline;
  flex-wrap: wrap;
}
.blackboard__signal-wrapper {
  display: flex;
  align-items: end;
  height: 5.625rem;
}
.blackboard__signal {
  width: 3rem;
}
.blackboard__space {
  width: 2rem;
}
</style>
