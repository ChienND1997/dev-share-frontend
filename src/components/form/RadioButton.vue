<template>
  <div class="mt-4 text-sm">
    <span class="text-gray-700 dark:text-gray-400">
      {{ radioLabel }}
    </span>
    <div class="mt-2">
      <label
        class="inline-flex items-center text-gray-600 dark:text-gray-400"
        v-for="(radio, index) in getRadioInputs"
        :key="radio.value"
        :class="{ 'ml-6': index > 0 }"
      >
        <input
          type="radio"
          class="text-purple-600 form-radio focus:border-purple-400 focus:outline-none focus:shadow-outline-purple dark:focus:shadow-outline-gray"
          :name="$utils.stringUtils.toKebabCase(radioLabel)"
          :value="radio.value"
          @change="$emit('update:modelValue', $event.target.value)"
        />
        <span class="ml-2">{{ radio.label }}</span>
      </label>
    </div>
  </div>
</template>

<script lang="ts">
export default defineComponent({
  props: {
    radioLabel: {
      type: String,
      default: "Radio Button Label",
    },
    modelValue: {
      type: Object as PropType<FormValueLabel>,
      required: true,
    },
  },
  computed: {
    getRadioInputs() {
      return [...this.modelValue];
    },
  },
});
</script>
