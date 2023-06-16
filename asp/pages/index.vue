<template>
  <h1 v-if="$auth.loggedIn" class="title" v-text="$auth.user.name"></h1>
  <h1 v-else>Hello</h1>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
