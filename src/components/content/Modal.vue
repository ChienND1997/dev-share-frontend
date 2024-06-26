<template>
  <!-- Modal modal-backdrop. This what you want to place close to the closing body tag -->
  <transition name="modal-backdrop">
    <div class="fixed inset-0 z-30 flex items-end bg-black bg-opacity-50 sm:items-center sm:justify-center">
      <!-- Modal -->
      <transition name="modal">
        <div
          @keydown.escape="emitClosedModal()"
          class="w-full px-6 py-4 overflow-hidden bg-white rounded-t-lg dark:bg-gray-800 sm:rounded-lg sm:m-4 sm:max-w-xl"
          role="dialog"
          id="modal"
        >
          <!-- Remove header if you don't want a close icon. Use modal body to place modal tile. -->
          <header class="flex justify-end">
            <button
              class="inline-flex items-center justify-center w-6 h-6 text-gray-400 transition-colors duration-150 rounded dark:hover:text-gray-200 hover: hover:text-gray-700"
              aria-label="close"
              @click="emitClosedModal()"
            >
              <element-svg aria-hidden="true" :class="'w-4 h-4'" :view-box="'0 0 20 20'" :fill="'currentColor'" :pic="'cross'" />
            </button>
          </header>
          <!-- Modal body -->
          <div class="mt-4 mb-6">
            <!-- Modal title -->
            <p class="mb-2 text-lg font-semibold text-gray-700 dark:text-gray-300" v-if="header">
              {{ header }}
            </p>
            <!-- Modal description -->
            <p class="text-sm text-gray-700 dark:text-gray-400" v-if="content">
              {{ content }}
            </p>
          </div>
          <footer
            class="flex flex-col items-center justify-end px-6 py-3 -mx-6 -mb-4 space-y-4 sm:space-y-0 sm:space-x-6 sm:flex-row bg-gray-50 dark:bg-gray-800"
          >
            <button
              @click="emitClosedModal()"
              v-if="cancel"
              class="w-full px-5 py-3 text-sm font-medium leading-5 text-white text-gray-700 transition-colors duration-150 border border-gray-300 rounded-lg dark:text-gray-400 sm:px-4 sm:py-2 sm:w-auto active:bg-transparent hover:border-gray-500 focus:border-gray-500 active:text-gray-500 focus:outline-none focus:shadow-outline-gray"
            >
              {{ cancel }}
            </button>
            <button
              v-if="ack"
              class="w-full px-5 py-3 text-sm font-medium leading-5 text-white transition-colors duration-150 bg-purple-600 border border-transparent rounded-lg sm:w-auto sm:px-4 sm:py-2 active:bg-purple-600 hover:bg-purple-700 focus:outline-none focus:shadow-outline-purple"
            >
              {{ ack }}
            </button>
          </footer>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script lang="ts">
export default defineComponent({
  props: {
    header: {
      type: String,
      default: "",
    },
    content: {
      type: String,
      default: "",
    },
    cancel: {
      type: String,
      default: "",
    },
    ack: {
      type: String,
      default: "",
    },
  },
  methods: {
    emitClosedModal(): void {
      this.$emit("closed-modal");
    },
  },
});
</script>

<style>
.modal-enter-active,
.modal-backdrop-enter-active {
  @apply transition ease-out duration-150;
}

.modal-enter-from,
.modal-leave-to {
  @apply opacity-0 transform translate-y-0.5;
}

.modal-enter-to,
.modal-leave-from,
.modal-backdrop-enter-to,
.modal-backdrop-leave-from {
  @apply opacity-100;
}

.modal-leave-active,
.modal-backdrop-leave-active {
  @apply transition ease-in duration-150;
}

.modal-backdrop-enter-from,
.modal-backdrop-leave-to {
  @apply opacity-0;
}
</style>
