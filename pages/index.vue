<template>
  <section class="daily_foods">
    <h5>Daily Foods>></h5>
    <div class="food_list">
      <img src="/Good.png" alt="" srcset="" />
    </div>
  </section>
</template>
  
<script>
export default {
  data() {
    return {
      food: [1, 2, 3],
    }
  },
  //   async fetch() {
  //  let doit= await $axios.get('www.themealdb.com/api/json/v1/1/random.php')
  //  console.log(doit);
  //   },
  methods: {
    goTo(user) {
      this.$router.push('/users/' + user)
    },
  },
}
</script>
  
<style lang="scss">
.daily_foods {
  margin-top: 5em;
}

.food_list img {
  width: 300px;
  height: 300px;
}
</style>