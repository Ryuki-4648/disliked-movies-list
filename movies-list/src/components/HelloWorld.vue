<template>
  <main>
    <div class="content">
      <section class="intro">
        <h1 class="page-title">{{ msg }}</h1>
        <p class="text01">あらすじを読んで「絶対見たくない」と心に誓った映画、<br>うっかり見てしまい「二度と見ない」と決心した映画を集めました。</p>
      </section>

      <section class="search">
        <p class="text02">あなたの、<br class="sp-only">「見たくない映画」はありますか？</p>
        <div class="search-area">
          <input type="text" placeholder="エイガ ノ タイトル ヲ ニュウリョク" class="search-box" v-model="vueSearch">
          <div class="search-btn-wrap">
            <button class="search-btn" @click="filterButton">サガす</button>
            <img src="../assets/img01.png" alt="" class="search-btn-img">
          </div>
          <p class="reset-btn" @click="resetButton">リセット</p>
        </div>
      </section>

      <section class="list">
        <ul class="movie-list">
          <li v-for="(movie, index) in movies" :key="index" class="movie-item">
            <p class="movie-title">{{ movie.title }}</p>
            <table class="movie-table">
              <tr>
                <th>あらすじ</th>
                <td v-html="movie.description"></td>
              </tr>
              <tr>
                <th>監督</th>
                <td>{{ movie.director }}</td>
              </tr>
              <tr>
                <th>見たくない理由</th>
                <td>{{ movie.reason }}</td>
              </tr>
            </table>
          </li>
        </ul>
      </section>
    </div>

    <footer>
      <div class="footer-content">
        <small>&copy; 2023 Disliked Movies List <br class="sp-only">by R.YUKI Portfolio</small>
        <img src="../assets/img02.png" alt="" class="footer-img">
      </div>
            <a href="" class="page-top" @click="scrollToTopButton">オサナイデ</a>
    </footer>
  </main>
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
    filterButton: function(){
      const searchVal = this.vueSearch;
      const filterData = this.movies.filter(function(movie){
        return movie.title.indexOf(searchVal) !== -1;
      });
      this.movies = filterData;
    },
    resetButton: function(){
      location.reload();
    },
    scrollToTopButton() {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
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
a {
  text-decoration: none;
}
.sp-only {
  display: none;
}
@media (max-width: 768px) {
  .pc-only {
    display: none;
  }
  .sp-only {
    display: block;
  }
}
.content {
  width: 1024px;
  margin: 0 auto;
  padding: 0;
  position: relative;
}
.page-title {
  letter-spacing: 0.05em;
}
.intro {
  margin: 0 auto 140px;
}
.text01 {
  line-height: 2;
  font-size: 15px;
}
.text02 {
  line-height: 2;
  font-size: 18px;
  margin: 0 auto 20px;
  letter-spacing: 0.1em;
}
@media (max-width: 1024px) {
  .content {
    width: 90%;
  }
  .intro {
    margin: 0 auto 80px;
  }
  .text01 {
    font-size: 14px;
  }
}

.search {
  margin: 0 auto 80px;
}
.search-area {
  display: flex;
  align-items: center;
}
.search-box {
  margin: 0 20px 0 0;
  border: 1px solid #ddd;
  width: 360px;
  height: 32px;
  padding: 1px 6px;
}
.search-btn {
  border: none;
  background-color: #d10b1e;
  color: #fff;
  font-size: 13px;
  letter-spacing: 0.05em;
  font-weight: 600;
  width: 120px;
  height: 28px;
  cursor: pointer;
  transition: all .3s;
  padding: 2px 0 0 0;
}
.search-btn:hover {
  background-color: #ba0620;
}
.search-btn:hover + .search-btn-img {
  bottom: -10px;
  transition: all .3s;
}
.search-btn-wrap {
  position: relative;
}
.search-btn-img {
  position: absolute;
  bottom: 0;
  right: 0px;
  width: 40px;
  z-index: -1;
}
@media (max-width: 768px) {
  .search-area {
    flex-wrap: wrap;
  }
  .search-box {
    margin: 0 0 20px;
    width: 100%;
  }
}

.reset-btn {
  font-size: 13px;
  color: #ba0620;
  cursor: pointer;
  transition: all .3s;
  margin: 0 0 0 30px;
}
.reset-btn:hover {
  color: #777;
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
@media (max-width: 768px) {
  .movie-title {
    font-size: 21px;
    margin: 0 auto 15px;
  }
  .movie-item {
    width: 100%;
    padding: 0 0 15px;
    margin: 0 0 30px;
  }
  .movie-table tr {
    flex-wrap: wrap;
    margin: 0 auto 15px;
  }
  .movie-table td {
    width: 100%;
  }
  .movie-table th {
    margin: 0 0 5px;
  }
}

.page-top {
  position: absolute;
  right: 30px;
  bottom: 80px;
  color: #000;
  font-size: 13px;
  transform: rotate(8deg);
  letter-spacing: 0.1em;
  transition: all .2s;
}
.page-top:hover {
  transform: rotate(20deg);
  color: #ba0620;
}
@media (max-width: 1500px) {
  .page-top {
    right: 20px;
    bottom: 100px;
  }
}
footer {
  padding: 150px 0 0;
  border-bottom: 20px solid #000;
  position: relative;
  overflow: hidden;
}
footer small {
  margin: 0 auto 10px;
  display: block;
}
.footer-content {
  width: 1024px;
  margin: 0 auto;
  position: relative;
}
.footer-img {
  position: absolute;
  right: 10px;
  bottom: -10px;
  cursor: pointer;
  transition: all 2500ms ease-in-out;
}
.footer-img:hover {
  bottom: -60px;
}
@media (max-width: 1024px) {
  footer {
    padding: 80px 0 0;
  }
  footer small {
    font-size: 10px;
  }
  .footer-content {
    width: 90%;
  }
}
</style>
