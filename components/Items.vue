<template>
  <div>
    <div class="flexi">
      <v-img
        v-for="item in items"
        :key="item"
        class="this"
        lazy-src="https://picsum.photos/id/11/10/6"
        max-height="150"
        max-width="250"
        src="https://picsum.photos/id/11/500/300"
      />
    </div>
  </div>
</template>
<script>
export default {
  props: {
    affessa: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      items: {
        primo: 'questo è il primo',
        sec: 'questo è il 2',
        ter: 'questo è il 3',
        ter2: 'questo è il 3',
        qua: 'questo è il 4'
      }
    }
  }
}
</script>
<style>
.flexi {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  background-color: rgb(167, 199, 24);
  justify-content: center;
}
.flexi > div {
  /* flex-direction: row; */
  /* margin: 10px; */
  content: "";
  margin: 5px;
}
</style>
