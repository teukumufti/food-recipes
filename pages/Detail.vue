<template>
  <b-container fluid class="container-detail">
    <b-card class="card-detail">
      <div class="title">
        <h5 class="mb-3">
          {{ recipes.title }}
        </h5>
        <b-img :src="recipes.thumb" class="img-detail" />
        <div class="desc">
          <span>
            {{ recipes.desc }}
          </span>
        </div>
      </div>

      <div class="ingredient">
        <h4 class="mb-3 text-center">Ingredient</h4>
        <div v-for="(item, index) in recipes.ingredient">
          <span>- {{ item }}</span> <br />
        </div>
        <div class="item">
          <span>
            Bahan Tambahan :
            <br />
            <br />
          </span>
          <div v-for="(item, index) in recipes.needItem">
            <span> - {{ item.item_name }}</span>
            <br />
            <br />
            <b-img :src="item.thumb_item" />
          </div>
        </div>
      </div>

      <div class="step">
        <h4 class="mb-4 text-center">Step</h4>
        <div v-for="(item, index) in recipes.step">
          <span>
            {{ item }}
          </span>
          <br />
        </div>
      </div>

      <div class="user">
        <b-row>
          <b-col class="date text-justify">
            <p>
              Servings : {{ recipes.servings }}
              <br />
              Times : {{ recipes.times }}
              <br />
              Dificulty : {{ recipes.dificulty }}
            </p>
          </b-col>
          <b-col class="caption text-right mt-3">
            <p v-if="recipes.author">
              Publish at : {{ recipes.author.datePublished }} <br />
              By : {{ recipes.author.user }}
            </p>
          </b-col>
        </b-row>
      </div>
    </b-card>
  </b-container>
</template>

<script>
export default {
  name: "detail",
  data() {
    return {
      recipes: [],
    };
  },
  mounted() {
    this.fetchRecipes();
  },
  methods: {
    async fetchRecipes() {
      const data = await this.$axios.$get(
        `https://masak-apa-tomorisakura.vercel.app/api/recipe/:${this.$route.query.key}`
      );
      this.recipes = data.results;
      console.log(data.results);
    },
  },
};
</script>

<style>
.container-detail {
  width: 80%;
  overflow: hidden;
  text-align: center;
}
.card-detail {
  background-color: rgb(255, 153, 0);
  margin: auto;
  margin-top: 20px;
}
.img-detail {
  width: 90%;
  margin-top: 20px;
  margin-bottom: 20px;
}

.desc {
  text-align: justify;
}
.ingredient {
  text-align: justify;
  margin-top: 40px;
}
.item {
  margin-top: 20px;
}
.step {
  text-align: justify;
  margin-top: 40px;
}
.user {
  margin-top: 70px;
}
</style>
