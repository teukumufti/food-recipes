<template>  
  <div>
  <b-navbar toggleable="sm" type="light" variant="light" class="Navbar">

    <b-navbar-brand class="nav-icon">
      <h1 class="title-nav">TIMPHAN</h1>
      <span class="text-nav">The Best Recipes Food</span>
    </b-navbar-brand>
  </b-navbar>
  </div>
</template>




<script>
export default {
  name: 'Navbar'
}
</script>

<style>

.Navbar {
  background-image: url("https://www.kamandaluresort.com/images/petulu.jpg");
  height: 34.5rem;
  background-repeat: no-repeat;
  background-size: 100%;
}

.nav-icon {
  margin: auto;
  color: rgb(255, 255, 255) !important;
  font-family: serif;
}

.title-nav{
  margin-left: 53px;
}.text-nav {
  letter-spacing: 5px;
}

@media only screen and (max-width: 1000px) {
.Navbar{
  height: 22rem !important;
  background-color: rgb(106, 1, 1) !important;

}
}
</style>

