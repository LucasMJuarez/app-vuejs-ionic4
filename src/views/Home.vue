<template>
<div>
  <ion-card v-for="post in posts" :key="post.data.id" style="border: 1px solid green"> 
    <ion-card-content>
      <template v-if="post.data.thumbnail.startsWith('https://')">
        <img :src="post.data.thumbnail" >
      </template>
      <ion-label color="light">{{post.data.title}} </ion-label>
      <ion-button color="light" expand="full" @click="viewMore(post.data)" >
        View More
      </ion-button>
    </ion-card-content>

  </ion-card>
</div>
</template> 

<script>
import axios from 'axios';

export default {
  data(){
    return{
      posts:[]
    }
  },
  async mounted() {
    const response = await axios.get('https://www.reddit.com/r/argentina.json');
    this.posts = response.data.data.children;
  },
  methods: {
    viewMore(post){
      this.$router.push({name: 'detail', params : { post }})
    }
  }
}
</script>

<style>
.thumb {
  width: 60px;
  height: 60px;
  border-radius: 30px;
  margin-right: 15px;
  margin-top: 10px;
  margin-bottom: 10px;
}
</style>