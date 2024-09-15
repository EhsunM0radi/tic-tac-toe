<template>
  <button class="bg-white border border-gray-400 text-center text-2xl font-bold rounded-md shadow-sm transition-transform transform hover:scale-105 w-20 h-20 m-1" @click="clickHandler">{{value}}</button>
</template>

<script>
export default {
  name: "square",
  props: ["index", "value"],
  methods: {
    clickHandler() {
      this.$emit("selection", { index: this.index });
    }
  }
};
</script>