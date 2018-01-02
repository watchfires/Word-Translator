<template>
  <h2 class="text-success">{{translatedText}}</h2>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
}
</script>

<style>

h2 {
  margin-top: 1.5rem;
}

</style>