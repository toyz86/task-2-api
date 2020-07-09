<template>
  <div class="container mt-5">
    <div class="d-flex">
        <div class="card-section overflow-auto" style="height: 300px" >
            <div class="card" v-for="post in posts" v-bind:Key="post.id">
                <h4 class="card-title">{{ post.title }}</h4>
                <p class="card-body">{{ post.body }}</p>
            </div>
        </div>
        <div class="card-section overflow-auto" style="height: 300px" >
            <div class="card" v-for="comment in comments" v-bind:Key="comment.id">
                <h4 class="card-title">{{ comment.name }}</h4>
                <span class="card-body">{{ comment.email }}</span>
                <p class="card-body">{{ comment.body }}</p>
            </div>
        </div>
        <div class="card-section overflow-auto" style="height: 300px" >
            <div class="card" v-for="album in albums" v-bind:Key="album.id">
                <h4 class="card-title">{{ album.id }}</h4>
                <span class="card-body">{{ album.title }}</span>
            </div>
        </div>        
    </div>
    <div class="d-flex">
        <div class="card-section overflow-auto" style="height: 300px" >
            <div class="card" v-for="photo in photos" v-bind:Key="photo.id">
                <h4 class="card-title">{{ photo.title }}</h4>
                <p class="card-body">{{ photo.body }}</p>
            </div>
        </div>
        <div class="card-section overflow-auto" style="height: 300px" >
            <div class="card" v-for="todo in todos" v-bind:Key="todo.id">
                <h4 class="card-title">{{ todo.name }}</h4>
                <p class="card-body">{{ todo.body }}</p>
            </div>
        </div>
        <div class="card-section overflow-auto" style="height: 300px" >
            <div class="card" v-for="user in users" v-bind:Key="user.id">
                <span class="card-body">{{ user.title }}</span>
            </div>
        </div>
    </div>    
  </div>

</template>

<script>
import axios from 'axios'

const reqOne = axios.get("https://jsonplaceholder.typicode.com/posts");
const reqTwo = axios.get("https://jsonplaceholder.typicode.com/comments");
const reqThree = axios.get("https://jsonplaceholder.typicode.com/albums");
const reqFour = axios.get("https://jsonplaceholder.typicode.com/photos");
const reqFive = axios.get("https://jsonplaceholder.typicode.com/todos");
const reqSix = axios.get("https://jsonplaceholder.typicode.com/users");
console.log('ini data posts', reqOne);
console.log('ini data comment', reqTwo);
console.log('ini data albums', reqThree);

export default {
    data () {
        return {
            posts: [],
            comments: [],
            albums: [],
            photos: [],
            todos: [],
            users: []
        }
    },

  mounted () {
    this.getApi();
  },
  methods: {
      getApi() {
        this.$nextTick(() => {
            this.$nuxt.$loading.start();
            axios
            .all([reqOne,reqTwo,reqThree,reqFour,reqFive,reqSix])
            .then(axios.spread((...responses) => {
                this.posts = responses[0].data;
                this.comments = responses[1].data;
                this.albums = responses[2].data;
                this.photos = responses[3].data;
                this.todos = responses[4].data;
                this.users = responses[5].data;
                this.$nuxt.$loading.finish();
            }));
        });
      }
  }
}
</script>

<style scoped>
.card-title {
    background-color: #c7c7c7;
    padding: 15px;
    margin-bottom: 0;
}

.card-body {
    padding: 15px;
}

.card-section {
    border: 1px solid #c0c0c0;
    margin: 5px;
} 

@media (min-width: 768px) {  
    .card-columns {column-count: 3;}
}

@media (min-width: 992px) { 
    .card-columns {column-count: 3;}
}

@media (min-width: 1200px) {  
    .card-columns {column-count: 3;} 
}
</style>
