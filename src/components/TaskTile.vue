<template>
  <div
    class="flex gap-4 py-2 px-5 justify-between bg-white dark:bg-slate-800 border-solid border-b-2 border-b-gray-400"
  >
    <div class="flex gap-4 items-center">
      <div class="">
        <input
          class="w-6 h-6 rounded-full items-center"
          type="checkbox"
          v-model="isChecked"
          @change="task.complete = isChecked"
        />
      </div>
      <p
        class="text-sky-900 dark:text-gray-200"
        :class="{ 'line-through': task.complete }"
      >
        {{ task.todo }}
      </p>
    </div>
    <div class="items-center flex" @click="deleteTodo">
      <i class="bx bx-x text-3xl text-gray-500 dark:text-gray-200"></i>
    </div>
  </div>
</template>

<script>
export default {
  props: ["task"],
  data() {
    return {
      isChecked: false,
    };
  },
  methods: {
    deleteTodo() {
      this.$emit("delete-todo", this.task.id);
    },
  },
  computed: {},
};
</script>

<style></style>
