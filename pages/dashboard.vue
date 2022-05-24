<template>
  <div class="container mt-5">
    <!-- Botão -->
    <Button _class="btn btn-sm-2 btn-success d-block mr-0 ml-auto mb-3" id="createModal">Create post</Button>
    <hr class="mt-0" />
    <!-- Modal | Criar post -->
    <div class="modal fade" id="createModal" tabindex="-1" role="dialog" aria-labelledby="createModal"
      aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Create post</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">

            <form @submit.prevent="createPost">

              <div class="form-group">
                <label for="title">Type the title:</label>
                <input type="text" v-model="title" class="form-control" placeholder="Title" maxlength="50" required>
              </div>

              <div class="form-group">
                <label for="author">Type the author name:</label>
                <input type="text" v-model="userAuthor" class="form-control" placeholder="Author name" required>
              </div>

              <div class="form-group">
                <label for="author">Type the description:</label>
                <input type="text" v-model="description" class="form-control" placeholder="Description" maxlength="100"
                  required>
              </div>

              <div class="form-group">
                <label for="author">Type the image link:</label>
                <input type="text" v-model="image" class="form-control" placeholder="Image link" required>
              </div>

              <div class="form-group">
                <label for="author">Type the content:</label>
                <textarea v-model="content" class="form-control" cols="10" rows="4" placeholder="Content"></textarea>
              </div>

              <div class="modal-footer">
                <button type="submit" class="btn btn-primary" style="background-color: #9545ed; border:#9545ed">Save
                  changes</button>
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
              </div>

            </form>

          </div>

        </div>
      </div>
    </div>
    <!-- Modal | Editar -->
    <div class="modal fade" id="editModal" tabindex="-1" role="dialog" aria-labelledby="createModal" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Edit post</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">

            <form @submit.prevent="editPost">

              <div class="form-group">
                <label for="title">Type the title:</label>
                <input type="text" v-model="editTitle" class="form-control" placeholder="Title" maxlength="50" required>
              </div>

              <div class="form-group">
                <label for="author">Type the author name:</label>
                <input type="text" v-model="edituserAuthor" class="form-control" placeholder="Author name" required>
              </div>

              <div class="form-group">
                <label for="author">Type the description:</label>
                <input type="text" v-model="editDescription" class="form-control" placeholder="Description"
                  maxlength="100" required>
              </div>

              <div class="form-group">
                <label for="author">Type the image link:</label>
                <input type="text" v-model="editImage" class="form-control" placeholder="Image link" required>
              </div>

              <div class="form-group">
                <label for="author">Type the content:</label>
                <textarea v-model="editContent" class="form-control" cols="10" rows="4"
                  placeholder="Content"></textarea>
              </div>

              <div class="modal-footer">
                <button type="submit" class="btn btn-primary" style="background-color: #9545ed; border:#9545ed">Save
                  changes</button>
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
              </div>

            </form>

          </div>

        </div>
      </div>
    </div>
    <!-- Card -->
    <div class="row justify-content-between">
      <div class="col-auto mb-3 d-flex align-items-stretch" v-for="post in posts" :key="post.id">
        <Card :title="post.title" :description="post.description" :image="post.image">

          <template v-slot:card-content>
            <div class="row d-flex justify-content-center">
              <button class="btn btn-outline-white" style="background-color: #9545ed; border:#9545ed;"
                @click="setData(post.title, post.content, post.userAuthor, post.image, post.description, post.id)">Edit</button>
              <button class="btn btn-outline-white" style="background-color: #9545ed; border:#9545ed;"
                @click="deletePost(post.id)">Delete</button>
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
        posts: '',

        editId: '',
        editTitle: '',
        editContent: '',
        edituserAuthor: '',
        editImage: '',
        editDescription: ''

      }
    },

    created() {
      this.getPosts()
    },

    methods: {

      async getPosts() {
        try {
          let response = await this.$axios.get('/post')
          this.posts = response.data.response
        } catch (err) {
          console.log(err)
        }
      },

      async createPost() {
        try {

          await this.$axios.post('/post', {
            title: this.title,
            content: this.content,
            userAuthor: this.userAuthor,
            image: this.image,
            description: this.description
          })

          $('#createModal').modal('hide')

          this.getPosts()
          this.clearInputs()


        } catch (err) {
          console.log(err)
        }
      },

      async deletePost(postId) {

        const confirm = window.confirm('Do you really want to delete this post?')

        if (confirm) {
          try {
            await this.$axios.delete(`/post/${postId}`)
            console.log('apagada com sucesso')

            this.getPosts()

          } catch (err) {
            console.log('erro')
          }
        }

      },

      async editPost() {
        try {
          await this.$axios.put(`/post/${this.editId}`, {
            title: this.editTitle,
            content: this.editContent,
            userAuthor: this.edituserAuthor,
            description: this.editDescription,
            image: this.editImage
          })

          $('#editModal').modal('hide')

          this.getPosts()

        } catch (err) {
          console.log(err)
        }
      },

      setData(title, content, userAuthor, image, description, id) {
        this.editTitle = title
        this.editContent = content
        this.edituserAuthor = userAuthor
        this.editImage = image
        this.editDescription = description
        this.editId = id

        $('#editModal').modal('show')

      },

      clearInputs() {
        this.title = ''
        this.content = ''
        this.description = ''
        this.userAuthor = ''
        this.image = ''
      }
    },

    head: {
      titleTemplate: 'Dashboard'
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
