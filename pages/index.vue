<template>
  <div class="container-fluid mt-6">
    <div class="row">
      <div class="col-lg-6">
        <div class="container flex-title">

          <h1 class="text text-center">Welcome to the Blog</h1><br />

          <center>
            <small class="description-text mb-4"><b>A simple Post Crud where a small blog was created to interact with
                the API! Enjoy it.</b></small><br>
          </center>

          <center>
            <small style="color: #172b4d;"><br>Contact me</small>
          </center>

          <div class="btn-wrapper text-center">
            <a href="https://github.com/LePetuconski" target="_blank" class="btn btn-neutral btn-icon mt-4"
              style="color:#8151e0">
              <i class="fa-brands fa-github"></i>
              <span class="btn-inner--text">Github</span>
            </a>
            <a href="https://www.linkedin.com/in/leticiapetuconski" target="_blank"
              class="btn btn-neutral btn-icon mt-4" style="color:#8151e0">
              <i class="fa-brands fa-linkedin"></i>
              <span class="btn-inner--text">LinkedIn</span>
            </a>
          </div>
        </div>
      </div>
      <div class="col-lg-6">
        <img src="../assets/img/blog-image.svg" class="img-fluid main-image" width="500" height="887">
      </div>
    </div>
  </div>

</template>

<script>

  export default {
    name: 'IndexPage',
  }

</script>

<style scoped>

  .flex-title {
    padding: 20% 12%;
    font-weight: bold;
    margin-right: 10%;
    margin-left: 1%;
    color: #ffffff;

  }

  .flex-title .text {
    font-size: 38.42px;
    color: #ffffff;
    background-color: #8151e0;
  }

  .description-text {
    font-size: 15px;
    color: #a46ae1;
  }

  .main-image {
    margin-top: 15%;
    margin-left: 4%;
  }

</style>
