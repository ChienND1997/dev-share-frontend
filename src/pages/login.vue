<template>
  <Title>Log in - {{ $utils.globals.projectName }}</Title>
  <auth-login />
</template>

<script lang="ts">
export default defineComponent({});
definePageMeta({
  layout: "non-auth-layout",
});
</script>
