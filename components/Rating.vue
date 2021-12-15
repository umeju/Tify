<template>
  <div>
    <v-rating
      v-model="rating"
      background-color="orange lighten-3"
      color="orange"
      size="16"
      class="stars"
    />
  </div>
</template>
<script>
export default {
  data: () => ({
    rating: 0
  })
}
</script>
<style>
.stars{
  margin: 0 0 0 -8px;
}
</style>
