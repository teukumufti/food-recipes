<template>
  <b-container fluid class="container-detail">
    <b-card class="card-detail">
      <div class="title">
        <h5 class="mb-3">
          {{ recipes.title }}
        </h5>
        <b-img :src="recipes.thumb" class="mb-4 mt-2" />
        <div class="desc">
          <span>
            {{ recipes.desc }}
          </span>
        </div>
      </div>

      <div class="ingredient">
        <h4 class="mb-3 text-center">Ingredient</h4>
        <div>
          <span>{{ recipes.ingredient }}</span> <br />
        </div>
        <div class="item">
          <span>
            Bahan Tambahan : <br />
            -{{ recipes.needItem }}
          </span>
          <br />
          <br />
          <b-img
            src="https://www.masakapahariini.com/wp-content/uploads/2019/05/bango-bumbu-kuliner-nusantara-nasi-goreng-kambing-khas-jakarta-100x100.png"
          />
        </div>
      </div>

      <div class="step">
        <h4 class="mb-3 text-center">Step</h4>
        <div>
          <span>
            {{ recipes.step }}
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
            <p>
              {{ recipes.author }}
              <!-- Publish at : februari 16 2020 <br />
              By : Valentina -->
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
