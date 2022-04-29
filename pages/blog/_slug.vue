<template>

  <div class="wrapper">
    <div class="top">
      <div class="title"></div>
    </div>
    <div class="content">
      <div class="card first">
        <h2 href="#"> {{ post.title }}</h2>
        <h4 href="#"> Author: {{ post.userAuthor }}</h4>
        <p class="date">{{ date }}</p>

        <img :src="post.image" :alt="post.title" class="img-fluid mb-1">
        <small>{{ post.description }}</small>
        <p class="text">{{ post.content}}</p>
      </div>

    </div>
  </div>

</template>

<script>
  export default {

    data() {
      return {
        post: '',
        slug: '',
        date: ''
      }
    },

    mounted() {
      this.slug = this.$route.params.slug
      this.getPost()
    },

    methods: {

      async getPost() {
        try {
          let response = await this.$axios.get(`/post/${this.slug}`)
          this.post = response.data.response
          this.date = new Date(response.data.response['createdAt']).toLocaleDateString('pt-BR', {
            day: '2-digit',
            month: 'long',
            year: 'numeric'
          })

        } catch (err) {
          console.log(err)
        }
      }
    }
  }

</script>

<style scoped>

  .top {
    background: #dbdbdb;
    height: 180px;

  }

  .content {
    padding-bottom: 20px;
  }

  .content .card.first {
    margin-top: -80px;
  }

  .card {
    position: relative;
    background: #fff;
    padding: 50px;
    width: 600px;
    margin: 20px auto 0 auto;
    box-shadow: 0 2px 4px rgba(100, 100, 100, .1);
  }

  .card h2 {
    font-size: 21px;
    font-weight: 500;
    color: #a46ae1;
    text-decoration: none;
  }

  .card .date {
    color: #9e9e9e;
    margin-top: 10px;
    font-size: 14px;
  }

  .card .text {
    color: #212121;
    margin-top: 20px;
    font-size: 15px;
    line-height: 22px;
  }

</style>
