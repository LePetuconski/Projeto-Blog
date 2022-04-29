<template>
  <div class="container mt-5">
    <div class="row justify-content-between">
      <div class="col-auto mb-3 d-flex align-items-stretch" v-for="post in posts" :key="post.id">
        <Card :title="post.title" :description="post.description" :image="post.image">

          <template v-slot:card-content>
            <div class="row d-flex justify-content-center">
              <NuxtLink :to="{name: 'blog-slug', params: {slug: post.slug}}" class="btn btn-outline-white"
                style="background-color: #9545ed; border:#9545ed;">Read more</NuxtLink>
            </div>
          </template>

        </Card>
      </div>
    </div>
  </div>
</template>



<script>
  import Card from '~/components/Card'
  import Button from '~/components/Button'

  export default {

    components: {
      Card,
      Button,
    },

    data() {
      return {
        title: '',
        content: '',
        userAuthor: '',
        description: '',
        image: '',
        posts: ''

      }
    },

    created() {
      this.getPosts()
    },


    methods: {

      async getPosts() {
        try {
          let response = await this.$axios.get(`/post`)
          this.posts = response.data.response

        } catch (err) {
          console.log(err)
        }
      }

    },

    head: {
      titleTemplate: 'Blog'
    }

  }

</script>

<style scoped>

  .card:hover {
    top: -3px;
    left: -3px;
    box-shadow: 3px 3px 15px 0px rgba(82, 82, 82, 0.85);
  }

  .card:active {
    top: 2px;
    left: 2px;
    box-shadow: inset 0 0 10px rgba(82, 82, 82, 0.85);
  }

</style>
