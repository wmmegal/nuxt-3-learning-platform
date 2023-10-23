<script setup lang="ts">
const { query } = useRoute()
const user = useSupabaseUser()

watch(user, () => {
  if (user.value) {
    return navigateTo(query.query)
  }
}, { immediate: true })
</script>

<template>

</template>