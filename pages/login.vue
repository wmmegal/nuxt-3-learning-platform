<script setup lang="ts">
const { title } = useCourse()
const supabase = useSupabaseClient()
const { query } = useRoute()
const login = async () => {
  const { error } = await supabase.auth.signInWithOAuth({
    provider: 'github',
    options: { redirectTo: `http://localhost:3000/confirm?query=${query.redirectTo}` }
  })
  if (error) {
    console.error(error)
  }
}
</script>

<template>
  <div class="prose w-full max-w-2xl h-9">
    <h1>Log in to {{ title }}</h1>
    <button
        @click="login"
        class="bg-blue-500 text-white font-bold py-2 px-4 rounded"
    >
      Log in with Github
    </button>
  </div>
</template>

