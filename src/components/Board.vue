<template>
  <div class="flex justify-center">
    <div class="grid grid-cols-3 gap-1">
      <square v-for="i in 9" :key="i-1" :index="i-1" :value="squares[i-1]" @selection="onSquareSelection"></square>
    </div>
  </div>
</template>

<script>
import Square from "./Square.vue";

export default {
  name: "board",
  components: {
    Square
  },
  props: ["squares"],
  methods: {
    onSquareSelection(event) {
      this.$emit("squareSelection", event);
    }
  }
};
</script>
