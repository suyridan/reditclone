<template>
  <div>
    <ion-card
    v-for="post in posts"
    :key="post.data.id"
    >
      <ion-card-content>
        <template v-if="post.data.thumbnail.startsWith('https://')">  
          <img :src="post.data.thumbnail" alt>
        </template>
        <ion-label color="light">
          {{ post.data.title }}
        </ion-label>
        <ion-button color="tertiary" expand="full" @click="viewMore(post.data)">
          Ver mas
        </ion-button>
      </ion-card-content>
      
    </ion-card>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      posts: []
    }
  },
  async mounted() {
      const response = await axios.get('https://www.reddit.com/r/marvelstudios.json')
      this.posts = response.data.data.children
  },
  methods:{
    viewMore(post){
      this.$router.push({
        name: 'detail',params: {post}  
      })
    }
  }
}

</script>
