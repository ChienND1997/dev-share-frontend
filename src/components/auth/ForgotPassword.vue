<template>
  <auth-image />
  <div class="flex items-center justify-center p-6 sm:p-12 md:w-1/2">
    <div class="w-full">
      <content-module-title :module-title="'Forgot password'" />
      <form-text-input :is-first-element="true" :input-label="'E-mail'" :place-holder="'made.with@love.me'" />
      <div class="w-full mt-4">
        <element-button :button-text="'Recover password'" :size="'regular'" :is-block-level="true" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default defineComponent({});
</script>
