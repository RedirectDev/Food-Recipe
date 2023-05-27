<template>
    <div>
        <div class="buttons">
            <button @click="fetchFood('Beef')"  type="button" class="btn btn-outline-dark"><img src="/cuisine/beef.png" alt="" srcset="">Beef</button>
            <button @click="fetchFood('Chicken')" type="button" class="btn btn-outline-dark"><img src="/cuisine/chicken.png" alt="" srcset="">Chicken</button>
            <button @click="fetchFood('Dessert')" type="button" class="btn btn-outline-dark"><img src="/cuisine/dessert.png" alt="" srcset=""> Dessert</button>
            <button @click="fetchFood('Lamb')" type="button" class="btn btn-outline-dark"><img src="/cuisine/lamb.png" alt="" srcset="">Lamb</button>
            <button @click="fetchFood('Pasta')" type="button" class="btn btn-outline-dark"><img src="/cuisine/pasta.png" alt="" srcset="">Pasta</button>
        </div>
  
        <div class="row food_categories">
            <nuxt-link class="col categories_link" v-for="meal in response" :key="meal.id" :to="`/${meal.idMeal}`">
                <img class="categories_img" :key="meal.id" :src="meal.strMealThumb" alt="" srcset="" />
                {{ meal.strMeal }}
            </nuxt-link>
   
        </div>

    </div>
</template> 
  
<script>
export default {
    data() {
        return { 
            response: [],
        };
    },
    created() {
        this.fetchFood('Beef');
    },
    methods: {
        async fetchFood(Beef) {
            try {
                const response = await this.$axios.get(`https://www.themealdb.com/api/json/v1/1/filter.php?c=${Beef}`);
                this.response = response.data.meals.splice(5, 4);
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script> 
  
<style lang="scss">
.buttons {
    display: flex;
    justify-content: space-evenly;
    align-items: center;

    button {
        background-color: #e24538;
        padding: .2em .5em;
        border: none;
        border-radius: .2em;
        font-size: 1.2em;
        font-weight: 700;
        color: #fff;
        img{
           margin-right: .5em;
            justify-content: center;
            align-items: center;
            width: 30px;
        }
     
    }

    img {
        width: 24px;
    }
}

.food_categories {
    cursor: pointer;
    display: flex;

}

.categories_link {
    margin-top: 2em;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    color: #000000;
    font-size: 1.2em;
    font-weight: 700;
    -webkit-text-decoration: none;
    text-decoration: none;
    transition: all 0.3s;

    &:hover {
        transform: translateY(-1em);
        text-decoration: none;
    }

    .categories_img {
        max-width: 250px;
        height: 250px;
        border-radius: 0.5em;
    }
}
</style>
  