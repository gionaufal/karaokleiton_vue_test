<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Users</h2>
    <div>
      <input type="text" v-model="input_val" @change='getVideos()'>
    </div>

    <p>Searching for: {{input_val}} karaoke</p>
    <ul>
      <li v-for="video in videos">
        <!-- <a href="http://youtube.com/watch?v={{video.videoId}}"> -->
        <!--   <img src="{{video.snippet.thumbnails.default.url}}" alt="image"> -->
        <!-- </a> -->
        id: {{video.id.videoId}}
        image: {{video.snippet.thumbnails.default.url}}
        name: {{video.snippet.title}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Karaokleiton',
      users: [
        {firstname: 'Sebastian', lastname: 'Eschweiler'},
        {firstname: 'Bill', lastname: 'Smith'},
        {firstname: 'John', lastname: 'Porter'}
      ],
      videos: [],
      input_val: ''
    }
  },

  methods: {
    getVideos(){
      var url = "https://www.googleapis.com/youtube/v3/search?part=snippet&q="
      url = url + this.input_val + 'karaoke' + "&key=AIzaSyDNtvz2GHiQJga-12qTPbbysPcRehON7V0"

      axios.get(url)
        .then(response => {
        this.videos = this.videos.concat(response.data.items)
          console.log(response.data.items[0].id.videoId)
        })
        .catch(error => {
          console.log(error)
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

a {
  color: #42b983;
}
</style>
