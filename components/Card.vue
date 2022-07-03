<template>  
 <b-container fluid class="Card">
    <h4 class="card-title">Find Your Favorite Food</h4>
  <div class="mt-4">
    <b-container fluid class="container-image">
      <b-img src="../assets/food2.jpg" fluid alt="Responsive image" class="card-image w3-animate-fading"></b-img>
    </b-container>
  </div>
</b-container>
</template>




<script>

export default {
  name: 'Card'
}
</script>

<style>
.Card {
    text-align: center !important;
}
.card-title{
    margin-top: 40px;
    color: white;
}
.container-image{
padding: 0px 0px 0;
 height: 400px;
 overflow: hidden;
 border-radius: 10px;

}
.card-image{
 width: 100%;
}

</style>