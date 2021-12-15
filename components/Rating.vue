<template>
  <div>
    <v-rating
      v-model="rating"
      background-color="orange lighten-3"
      color="orange"
      size="16"
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
