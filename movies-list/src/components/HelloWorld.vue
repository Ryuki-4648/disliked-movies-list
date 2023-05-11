<template>
  <div class="content">
    <h1 class="page-title">{{ msg }}</h1>
    <p class="text01">あらすじを読んで「絶対見たくない」と心に誓った映画、<br>うっかり見てしまい「二度と見ない」と決心した映画を集めました。</p>

    <p class="text02">あなたの、「見たくない映画」はありますか？</p>
    <div class="search-area">
      <input type="text" placeholder="エイガ ノ タイトル ヲ ニュウリョク" class="search-box" v-model="vueSearch">
      <button class="search-btn" @click="getFilterOutput">サガす</button>
    </div>
    <ul class="movie-list">
      <li v-for="(movie, index) in movies" :key="index" class="movie-item">
        <p class="movie-title">{{ movie.title }}</p>
        <table class="movie-table">
          <tr>
            <th>作品について</th>
            <td>{{ movie.description }}</td>
          </tr>
          <tr>
            <th>見たくない理由</th>
            <td>{{ movie.reason }}</td>
          </tr>
        </table>
      </li>
    </ul>
  </div>
</template>

<script>
import moviesList from '../data/moviesList.json';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      movies: moviesList,
      vueSearch: ''
    };
  },
  methods: {
    getFilterOutput: function(){
      const searchVal = this.vueSearch;
      const filterData = this.movies.filter(function(movie){
        return movie.title.indexOf(searchVal) !== -1;
      });
      this.movies = filterData;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
p {
  letter-spacing: 0.05em;
}
.page-title {
  letter-spacing: 0.05em;
}
.text01 {
  line-height: 2;
  font-size: 15px;
  margin: 0 auto 100px;
}
.text02 {
  line-height: 2;
  font-size: 18px;
  margin: 0 auto 20px;
  letter-spacing: 0.1em;
}
.content {
  width: 1024px;
  margin: 0 auto;
}
.search-area {
  margin: 0 auto 100px;
}
.search-box {
  margin: 0 20px 0 0;
  border: 1px solid #ddd;
  width: 320px;
  height: 28px;
  padding: 1px 6px;
}
.search-btn {
  border: none;
  background-color: #d10b1e;
  color: #fff;
  font-size: 13px;
  letter-spacing: 0.05em;
  font-weight: 600;
  width: 100px;
  height: 27px;
  cursor: pointer;
  transition: all .3s;
}
.search-btn:hover {
  background-color: #ba0620;
}
.movie-title {
  font-size: 24px;
  font-weight: 600;
  margin: 0 auto 30px;
}
.movie-table th {
  text-align: left;
  width: 130px;
  font-size: 15px;
}
.movie-table tr {
  margin: 0 auto 10px;
  display: flex;
  font-size: 18px;
}
.movie-table td {
  width: calc(100% - 130px);
  text-align: left;
  font-size: 14px;
  line-height: 1.8;
}
.movie-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.movie-item {
  width: 48%;
  border-bottom: 1px solid #ddd;
  box-sizing: border-box;
  padding: 0 0 30px;
  margin: 0 0 50px;
}
</style>
