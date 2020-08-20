<template>
  <div class="todo w-2/3 m-auto grid grid-flow-row grid-cols-3">
    <div
      class="todo-item flex-1 bg-gray-700 m-4 rounded-md shadow divide-y divide-gray-400"
    >
      <div class="task-title py-2 pl-4 pr-2 flex items-center">
        <div class="flex-grow-3 text-left">
          <input
            type="text"
            class="w-5/6 focus:outline-none bg-gray-700 border border-gray-400 rounded-md py-1 px-2"
            placeholder="Title"
          />
        </div>
        <div
          class="flex-grow-1 rounded-md py-1 cursor-pointer bg-blue-500 hover:bg-blue-700"
        >
          add
        </div>
      </div>
      <div class="task-content p-4 text-left">
        <textarea
          style="resize: none;"
          class="w-full focus:outline-none bg-gray-700 border border-gray-400 rounded-md p-2"
          rows="5"
          placeholder="Content"
        />
      </div>
    </div>
    <div
      class="todo-item flex-1 bg-gray-700 m-4 rounded-md shadow divide-y divide-gray-400"
      v-for="(item, index) in state.tasks"
      :key="index"
    >
      <div class="task-title py-2 pl-4 pr-2 flex items-center">
        <div class="flex-grow-3 text-left">{{ item.title }}</div>
        <div
          class="flex-grow-1 rounded-md py-1 cursor-pointer"
          :class="{
            'bg-red-500 hover:bg-red-700': item.status === 'todo',
            'bg-yellow-500 hover:bg-yellow-700': item.status === 'doing',
            'bg-green-500 hover:bg-green-700': item.status === 'done',
          }"
        >
          {{ item.status }}
        </div>
      </div>
      <div class="task-content p-4 text-left">{{ item.content }}</div>
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

<style lang="scss" scoped>
.todo-item {
  height: 15rem;
}
</style>
