<template>
  <div class="app">
    <h1>5월 마지막 영화 예매 순위</h1>
    <ul class="moives">
      <li v-for="movie in movies" :key="movie.id" class="item">
        <span class="rank">{{ movie.id }}</span>
        <router-link :to="{ name: 'show', params: { id: movie.id }}">
          <img v-bind:src="movie.poster" class="poster" />
        </router-link>
        <div class="detail">
          <strong cass="tit">{{movie.name}}</strong>
          <span class="rate">예매율 <span class="num">{{movie.rate}}</span></span>
          <router-link
           :to="{ name: 'show', 
           params: { id: movie.id}}" class="link"
           >자세히보기</router-link>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  created(){
    this.$http.get('/api/movies')
    .then((response) => {
      this.movies = response.data;
    }).catch(err => {
      alert(err);
      console.log(err);
    })
  },
  data(){
    return {
      movies: []
    }
  }
}
</script>

<style>
 
</style>