<template>
  <ul class="info_list">
    <InfoListitem
      v-for="movie in movies"
      :key="movie.id"
      :movie="movie"
      @handleTrash="$emit('handleTrash', movie.id)"
      @favourite="$emit('favourite', movie.id)"
    />
  </ul>
</template>
<script>
import InfoListitem from "../infoListItem/InfoListitem.vue";
export default {
  components: {
    InfoListitem,
  },
  props: {
    movies: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style>
</style>