<template>
  <div>
    <Navbar />
    <Nuxt />
  </div>
</template>

<script>
  export default {
    head: {
      link: [{
          rel: 'stylesheet',
          href: 'https://cdn.jsdelivr.net/npm/argon-dashboard@1.2.0/assets/css/argon.css'
        },
        {
          rel: 'stylesheet',
          href: 'https://cdn.jsdelivr.net/npm/argon-dashboard@1.2.0/assets/vendor/nucleo/css/nucleo.css'
        },
        {
          rel: 'stylesheet',
          href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css'
        },
      ],
      script: [{
          src: 'https://code.jquery.com/jquery-3.6.0.min.js'
        },
        {
          src: 'https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js'
        },
        {
          src: 'https://cdn.jsdelivr.net/npm/argon-dashboard@1.2.0/assets/js/argon.min.js'
        }
      ]
    }
  }

</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

  body {
    font-family: 'Poppins', sans-serif;
  }

</style>
