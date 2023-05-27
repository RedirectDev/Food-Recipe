<template>
  <section>
    <div class="foods">
      <h4>Daily Foods>></h4>
      <div class="row list">
        <DailyFoods />
        <DailyFoods />
        <DailyFoods />
        <DailyFoods />
      </div>
      <div>
        <h4>What You Wan't Now>></h4>
        <FoodCategories />
      </div>
      <div>
        <h4>Favorite Cuisine>></h4>
        <AreaCategories />
      </div>
    </div>
  </section>
</template>


<script>


export default {

}
</script> 

<style lang="scss">
h4 {
  color: #e24538;
  font-weight: 700;
  margin: 2em 0;
}

a {
  &:hover {
    color: #000000;
  }
}

.foods {
margin-bottom: 10em;
  .list {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
}
</style> 