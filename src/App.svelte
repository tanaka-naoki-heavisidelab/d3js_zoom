<script lang="ts">
  export let name: string;
</script>

<template lang="pug">
 main 
   h1 Hello {name}!
   p Visit the 
   |
   |
   a(href="https://svelte.dev/tutorial") Svelte tutorial
   |
   | to learn how to build Svelte apps.
</template>

<style src="./App.scss">
</style>
