<template>
  <div class="app container">
    <MoviInfo
      :movies="movies"
      :favouriteCount="movies.filter((e) => e.favourite).length"
    />
    <div class="movie_search">
      <SearchPanel :updateTerm="updateTerm"/>
      <div class="btns">
        <Buttons/>
      </div>
    </div>
    <MovieAddForm @createMovie="createMovie" />
    <div class="info-list">
      <InfoList @handleTrash="onRemove" @favourite="onFav" :movies="onSearch(movies, term)"/>
    </div>
  </div>
</template>
<script>
import MoviInfo from "./components/moviInfo/MoviInfo.vue";
import SearchPanel from "./components/searchPanel/SearchPanel.vue";
import Buttons from "./components/buttons/Buttons.vue";
import MovieAddForm from "./components/movieAddForm/MovieAddForm.vue";
import InfoList from "./components/infoList/InfoList.vue";
import axios from "axios"

export default {
  data() {
    return {
      movies: [
        
      ],
      term: '',
    };
  },
  methods: {
    createMovie(item) {
      this.movies.push(item);
    },
    onRemove(id) {
      this.movies = this.movies.filter((e) => e.id !== id);
    },
    onSearch(arr, term) {
      if(term.length === 0) {
        return arr
      }
      return arr.filter(e => e.name.toLowerCase().indexOf(term) > -1)
    },
    updateTerm(term) {
      this.term = term
    },
    async getData() {
      try{
        const {data} = await axios.get(`https://jsonplaceholder.typicode.com/posts`)
        const foundedData = data.map((element) => ({
          id: element.id,
          name: element.title,
          view: element.id,
          favourite: false
        }))
        this.movies = foundedData
        console.log(foundedData);
    }catch(error) {
      alert(error.message)
    }
  }
  },
  mounted() {
    this.getData()
  },
  components: {
    MoviInfo,
    SearchPanel,
    Buttons,
    MovieAddForm,
    InfoList,
  },
};
</script>
<style>
.box {
  display: flex;
  align-items: center;
}
.movie_search {
  padding: 40px;
  box-shadow: 10px 5px 5px rgb(1, 53, 16);
  margin-top: 40px;
}
.btns {
  margin-top: 40px;
}
.info-list {
  padding: 10px;
  box-shadow: 10px 5px 5px rgb(1, 53, 16);
  margin-top: 60px;
  margin-bottom: 100px;
}
</style>