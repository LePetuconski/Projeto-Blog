<template>
  <nav class="navbar navbar-horizontal navbar-expand-lg navbar-dark"
    style="background-color: #9545ed; border-color: #9545ed;">
    <div class="container">
      <NuxtLink class="navbar-brand" to="/">Blog</NuxtLink>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbar-default"
        aria-controls="navbar-default" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbar-default">
        <div class="navbar-collapse-header">
          <div class="row">
            <div class="col-6 collapse-brand">
              <a href="javascript:void(0)">
                <img src="#">
              </a>
            </div>
            <div class="col-6 collapse-close">
              <button type="button" class="navbar-toggler" data-toggle="collapse" data-target="#navbar-default"
                aria-controls="navbar-default" aria-expanded="false" aria-label="Toggle navigation">
                <span></span>
                <span></span>
              </button>
            </div>
          </div>
        </div>

        <ul class="navbar-nav ml-lg-auto">
          <li class="nav-item">
            <NuxtLink class="navbar-text nav-link" style="font-size: 16.5px;" to="/">
              <i class="fa-solid fa-house mr-1 ml-0"></i> Home
            </NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink class="nav-link navbar-text" style="font-size: 16.5px;" to="/blog">
              <i class="fa-regular fa-image"></i> Blog
            </NuxtLink>
          </li>
          <li class="nav-item dropdown">
            <NuxtLink class="nav-link navbar-text" style="font-size: 16.5px;" to="/dashboard">
              <i class="fas fa-bookmark"></i> Dashboard
            </NuxtLink>
            <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbar-default_dropdown_1">

            </div>
          </li>
        </ul>

      </div>
    </div>
  </nav>
</template>
