<template>
  <b-container fluid class="container-list">
    <div class="card-list">
      <b-col
        class="col-list"
        v-for="(item, index) in recipes"
        :key="item.key"
        @click="goToDetail(item.key)"
      >
        <b-card
          :img-src="item.thumb"
          img-alt="List image"
          img-left
          class="image-list"
        >
          <h5 class="title-list">
            {{ item.title }}
          </h5>
          <div class="text-list">
            <span> Times : {{ item.times }} </span>
            <br />
            <span> Portion : {{ item.portion }} </span>
            <br />
            <span> Dificulty : {{ item.dificulty }} </span>
          </div>
        </b-card>
      </b-col>
    </div>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      recipes: [],
    };
  },
  mounted() {
    this.fetchRecipes();
  },
  methods: {
    goToDetail(key) {
      this.$router.push({ path: "detail", query: { key } });
    },
    async fetchRecipes() {
      const data = await this.$axios.$get(
        "https://masak-apa-tomorisakura.vercel.app/api/recipes"
      );
      this.recipes = data.results;
      console.log(data.results);
    },
  },
};
</script>

<style>
.container-list {
  margin-top: 100px;
}
.card-list {
  display: flex;
  flex-wrap: wrap;
  /* flex-direction: row; */
}
.col-list {
  margin-top: 10px;
  height: auto;
}
.image-list {
  cursor: pointer;
  background-color: rgb(255, 153, 0);
  margin-top: 0px;
  height: 100%;
  border: 0px solid;
}
.title-list {
  margin-top: 0px;
  color: black;
}
.text-list {
  margin-top: 15px;
  font-family: sans-serif;
}
</style>
