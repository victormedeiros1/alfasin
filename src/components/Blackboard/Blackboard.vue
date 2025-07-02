<script setup lang="ts">
import { computed, ref, defineProps } from "vue";
import { signals } from "@/utils";

const props = defineProps<{ text: string; toggleCharacters: boolean }>();
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
          <span v-if="signal === ' '" class="blackboard__space"></span>
          <div v-else>
            <img
              class="blackboard__signal"
              :src="`/src/assets/images/${signal}.jpg`"
            />
            <div v-if="toggleCharacters" class="blackboard__character">
              {{ signal }}
            </div>
          </div>
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
  position: relative;
  display: flex;
  align-items: end;
  margin-bottom: 1rem;
}
.blackboard__space {
  width: 3rem;
}
.blackboard__signal {
  width: 6rem;
  height: 6rem;
}
.blackboard__character {
  position: absolute;
  bottom: -0.5rem;
  left: 50%;
  transform: translateX(-50%);
}

@media (max-width: 800px) {
  .blackboard__signal {
    width: 3rem;
    height: 3rem;
  }
}
</style>
