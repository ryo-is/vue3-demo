<template>
  <div class="modal-component">
    <button
      class="px-4 py-2 mx-2 font-bold text-white bg-green-500 rounded hover:bg-green-700 focus:outline-none"
      @click="toggleModal(true)"
    >
      Modal Open
    </button>
    <Teleport to="#teleport-modal">
      <div
        v-if="state.modal"
        class="modal absolute top-0 left-0 w-full h-full bg-gray-900 bg-opacity-50 flex flex-col items-center justify-center"
      >
        <div
          class="content bg-gray-400 p-4 w-1/3 h-64 flex flex-col items-center justify-center"
        >
          <button
            class="px-4 py-2 mx-2 font-bold text-white bg-red-500 rounded hover:bg-red-700 focus:outline-none"
            @click="toggleModal(false)"
          >
            Modal Close
          </button>
        </div>
      </div>
    </Teleport>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'

const state = reactive({
  modal: false,
})
const toggleModal = (value?: boolean) => {
  state.modal = value ? value : !state.modal
}

export default defineComponent({
  setup() {
    return {
      state,
      toggleModal,
    }
  },
})
</script>
