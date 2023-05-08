<template>
  <div class="content">
    <h1>{{ msg }}</h1>
    <p>あらすじを読んで「絶対見たくない」と心に誓った映画、<br>うっかり見てしまい「二度と見ない」と決心した映画。</p>
    <h3></h3>
    <!-- <ul>
      <li><a href="" target="_blank" rel="noopener">babel</a></li>
      <li><a href="" target="_blank" rel="noopener">eslint</a></li>
    </ul> -->
    <ul>
      <li>
        <p>映画名</p>
        <table class="movie-table">
          <tr>
            <th>作品の説明</th>
            <td></td>
          </tr>
          <tr>
            <th>見たくない理由</th>
            <td></td>
          </tr>
        </table>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
.movie-table th {
  text-align: left;
}
.movie-table tr {
  margin: 0 auto 10px;
  display: flex;
  font-size: 18px;
}
</style>
