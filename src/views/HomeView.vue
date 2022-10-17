<template>
  <div class="home">
      <Card  v-for="char in chars.results" :key="char.id" class="card" :image="char.image" :name="char.name" :status="char.status" />
  </div>
</template>

<script>
// @ is an alias to /src
import Card from '@/components/Card.vue'

export default {
  name: 'HomeView',
  data(){
    return{
      chars: {},
    }
  },
  components: {
    Card
  },
  mounted(){
    fetch("https://rickandmortyapi.com/api/character/")
    .then(res => res.json())
    .then(data => {
      this.chars = data;
    })
    .catch(err => console.error(err))
  }
}
</script>

<style>
.home{
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  max-width: 1200px;
  margin: 0 auto;
}

.card{
  border-radius: 15px;
  width: calc((100% / 4) - 30px);
  max-height: calc(100% - 20px);
  color: white;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.3);
  margin: 0 auto;
  margin-bottom: 20px;
}

.card:hover{
  transform: scale(1.05);
  transition: ease .45s;
}

.card img{
  width: 100%;
  border-radius: 15px 15px 0 0;
}

.Alive{
  background: rgb(113, 209, 113);
}
.Dead{
  background: rgb(218, 95, 95);
}
.unknown{
  background: rgb(132, 132, 132);
}
</style>