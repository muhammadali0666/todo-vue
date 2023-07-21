<template>
  <li class="item d-flex align-items-center justify-content-between">
    <span class="list-group-item-label"> {{ movie.name }} </span>
    <div class="box d-flex align-items-center">
      <input type="number" class="list-group-item-input" defaultValue="900" :value="movie.view"/>
      <div class="d-flex justify-content-center align-items-center">
        <button class="btn-cookie btn-sm ms-3" type="button" @click="$emit('favourite', movie.id)">
          <i class="fas fa-cookie"></i>
        </button>
        <button class="btn-trash btn-sm ms-3" type="button" @click="$emit('handleTrash', movie.id)">
          <i class="fas fa-trash"></i>
        </button>
        <i class="fas fa-star star-item"></i>
      </div>
    </div>
  </li>
</template>
<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true
    }
  }
};
</script>
<style>
.item {
  border-bottom: 1px solid #000;
  padding-bottom: 5px;
  padding-top: 5px;
}
.list-group-item-input {
  border-radius: 8px;
  padding: 4px;
  border: none;
  background-color: transparent;
}
.btn-cookie {
  border: none;
  color: #e09f3e;
}
.btn-trash {
  border: none;
  color: #e5383b;
}
.star-item {
  width: 3px;
  height: 35px;
  text-align: center;
  line-height: 35;
  font-size: 16px;
   color: #ffd700;
   transition: 0.3s all;
   transform: translate(30px);
   opacity: 0;
}
.star-item .like {
  transform: translate(30px);
   opacity: 1;
}
</style>