<template>
  <div class="kino">
    <h1 class="movi_info mt-5">Barcha kinolar soni:{{ movies.length }}</h1>
    <p class="fovourite">Sevimli film {{ favouriteCount }}</p>
    <button class="button-home" @click="handleMode">mode</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      handleMode() {
        if (document.body.classList.contains("dark")) {
          document.body.classList.remove("dark");
        } else {
          document.body.classList.add("dark");
        }
      },
    };
  },
  props: {
    movies: {
      type: Array,
      required: true,
    },
    favouriteCount: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style style>
.kino {
  box-shadow: 10px 5px 5px rgb(1, 53, 16);
  padding: 30px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.movi_info {
  margin-top: 100px;
}
.fovourite {
  font-size: 30px;
  font-weight: 500;
}
.button-home{
  border-radius: 1px solid #000;
  border-radius: 16px;
  background-color: #fff;
  padding: 5px 10px;
}
.button-home:hover {
  transition: all 0.3s ease;
  background-color: #000000;
  color: #ffffff;
  cursor: cell;
}
</style>