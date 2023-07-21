<template>
  <div class="movie-add-form">
    <h3 class="new-film">Yangi kino qo'shish</h3>
    <form class="add-form d-flex mt-3 align-items-center" @submit.prevent>
      <input
        :value="name"
        @input="name = $event.target.value"
        type="text"
        class="form-control"
        placeholder="Qanday kino?"
      />
      <input
        :value="view"
        @input="view = $event.target.value"
        type="number"
        class="form-control"
        placeholder="Nechi marotaba ko'rilgan?"
      />
      <button class="btn btn-outline-dark" type="submit" @click="handleData">Qo'shish</button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      view: "",
    };
  },
  methods: {
    handleData() {
      const newMovie = {
        name: this.name,
        view: this.view,
        favourite: false,
      };
      if(!this.name || !this.view) return
      this.$emit("createMovie", newMovie)
      this.name = ''
      this.view = ''
    },
  },
};
</script>
<style>
.movie-add-form {
  padding: 40px;
  box-shadow: 10px 5px 5px rgb(1, 53, 16);
  margin-top: 40px;
}
</style>