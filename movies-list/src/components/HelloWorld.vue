<template>
  <div class="content">
    <h1>{{ msg }}</h1>
    <p>あらすじを読んで「絶対見たくない」と心に誓った映画、<br>うっかり見てしまい「二度と見ない」と決心した映画。</p>
    <ul class="movie-list">
      <li v-for="(movie, index) in moviesList" :key="index" class="movie-item">
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
      moviesList: moviesList
    };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
p {
  line-height: 2;
  font-size: 15px;
  letter-spacing: 0.05em;
}
.content {
  width: 1024px;
  margin: 0 auto;
}
.movie-title {
  font-size: 21px;
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
