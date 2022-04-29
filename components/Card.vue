<template>
  <div class="card" style="width: 18rem">
    <img class="card-img-top" :src="image" />
    <div class="card-body">
      <h2 class="card-title">{{ title }}</h2>
      <p class="card-text">{{ description }}</p>
    </div>
    <div class="card-footer border-0" style="background-color: white">
      <slot name="card-content"></slot>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['title', 'description', 'image'],
  }

</script>

<style scoped>
</style>
