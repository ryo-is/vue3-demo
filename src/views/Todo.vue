<template>
  <div class="grid w-2/3 grid-flow-row grid-cols-3 m-auto todo">
    <div
      class="flex-1 h-56 m-4 bg-gray-700 divide-y divide-gray-400 rounded-md shadow todo-item"
    >
      <div class="flex items-center py-2 pl-4 pr-2 task-title">
        <div class="text-left flex-grow-3">
          <input
            type="text"
            class="w-5/6 px-2 py-1 bg-gray-700 border border-gray-400 rounded-md focus:outline-none"
            placeholder="Title"
          />
        </div>
        <div
          class="py-1 bg-blue-500 rounded-md cursor-pointer flex-grow-1 hover:bg-blue-700"
        >
          add
        </div>
      </div>
      <div class="p-4 text-left task-content">
        <textarea
          style="resize: none;"
          class="w-full p-2 bg-gray-700 border border-gray-400 rounded-md focus:outline-none"
          rows="5"
          placeholder="Content"
        />
      </div>
    </div>
    <div
      class="flex-1 m-4 bg-gray-700 divide-y divide-gray-400 rounded-md shadow todo-item"
      v-for="(item, index) in state.tasks"
      :key="index"
    >
      <div class="flex items-center py-2 pl-4 pr-2 task-title">
        <div class="text-left flex-grow-3">{{ item.title }}</div>
        <div
          class="py-1 rounded-md cursor-pointer flex-grow-1"
          :class="{
            'bg-red-500 hover:bg-red-700': item.status === 'todo',
            'bg-yellow-500 hover:bg-yellow-700': item.status === 'doing',
            'bg-green-500 hover:bg-green-700': item.status === 'done',
          }"
        >
          {{ item.status }}
        </div>
      </div>
      <div class="p-4 text-left task-content">{{ item.content }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

type Task = {
  title: string;
  status: 'done' | 'doing' | 'todo';
  content: string;
};

type State = {
  tasks: Task[];
};

export default defineComponent({
  name: 'todo',
  setup() {
    const state: State = reactive({
      tasks: [
        { title: 'todo_1', status: 'todo', content: 'hogehoge' },
        { title: 'todo_2', status: 'doing', content: 'hogehoge' },
        { title: 'todo_3', status: 'done', content: 'hogehoge' },
        { title: 'todo_4', status: 'done', content: 'hogehoge' },
      ],
    });

    return {
      state,
    };
  },
});
</script>

<style lang="scss" scoped></style>
