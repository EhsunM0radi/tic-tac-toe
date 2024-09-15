<template>
  <div class="flex flex-col items-center">
    <ul class="list-disc pl-5 space-y-1">
      <li v-for="(entry, move) in history" :key="move">
        <button @click="moveTo(move)" :class="{'bg-blue-500 text-white': isCurrentStep(move), 'bg-gray-200': !isCurrentStep(move)}"
          class="px-4 py-2 rounded transition-colors duration-300 hover:bg-blue-600 focus:outline-none">
          {{ buttonCaption(move, entry) }}
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "moves",
  props: ["history", "currentStep"],
  methods: {
    moveTo(move) {
      this.$emit("move", move);
    },
    buttonCaption: function(move, entry) {
      if (move === 0) {
        return `New Game`;
      }
      if (move > 0 && entry.position !== null) {
        return `Go to move #${move} 
        (Row: ${entry.position.row} Column: ${entry.position.col})`;
      }
    },
    isCurrentStep(move) {
      return move === this.currentStep;
    }
  }
};
</script>

<style scoped>
.highlight {
  font-weight: bold;
}
</style>

