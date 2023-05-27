<template>
  <section class="food">
    <nuxt-link class=" food_daily_link" v-for="meal in response" :key="meal.id" :to="`/${meal.idMeal}`">
      <img class="daily_img" :key="meal.id" :src="meal.strMealThumb" alt="" srcset="" />
      {{ meal.strMeal }}
    </nuxt-link>
  </section>
</template>
  
<script>
export default {
  data() {
    return {
      response: [],

    };
  },


  async fetch() {
    try {
      const response = await this.$axios.get('https://www.themealdb.com/api/json/v1/1/random.php');
      let doit = response.data;
      console.log(doit.meals[0]);
      this.response = doit.meals;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
  
<style lang="scss">
.food {
  position: relative;
  z-index: 1;
  width: 15em;
  cursor: pointer;
  display: flex;
  justify-content: space-between;

  .food_daily_link {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    color: #000000;
    font-size: 1.2em;
    font-weight: 700;
    text-decoration: none;
    transition: all .3s ease-in-out;

    &:hover {
      transform: translateY(-1em);
    }

    .daily_img {
      max-width: 250px;
      height: 250px;
      border-radius: .5em;
    }

  }




}
</style>
  