<template>
  <div
    v-if="tasks.length === 0 ? false : true"
    class="flex justify-between bg-white gap-4 text-gray-400 py-2 px-5 dark:bg-slate-800"
  >
    <p v-if="getNumberOfItems === 0">No item left</p>
    <p v-else>
      {{ getNumberOfItems }}
      {{ getNumberOfItems === 1 ? "item" : "items" }} left
    </p>
    <div class="x-sm:block hidden">
      <span
        v-for="(tab, index) in tabs"
        :key="index"
        class="inline-block mx-1 cursor-pointer"
        :class="{
          'text-blue-500': activeBtn === tab,
          'text-gray-400': activeBtn !== tab,
        }"
        @click="toggleButton(tab)"
        >{{ tab }}</span
      >
    </div>
    <p class="cursor-pointer" @click="$emit('delete-complete-todo')">
      Clear Completed
    </p>
  </div>
</template>

<script>
export default {
  props: ["tasks", "tabs"],
  data() {
    return {
      activeBtn: this.tabs[0],
    };
  },
  methods: {
    toggleButton(tabBtn) {
      this.activeBtn = this.activeBtn === tabBtn ? null : tabBtn;
      this.$emit("toggle-button", tabBtn);
    },
  },
  computed: {
    getNumberOfItems() {
      let numberOfItem = this.tasks.filter((task) => task.complete !== true);
      return numberOfItem.length;
    },
  },
};
</script>

<style></style>
