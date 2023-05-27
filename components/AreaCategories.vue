<template>
    <div>
        <div class="buttons">
            <button @click="fetchFood('Canadian')"  type="button" class="btn btn-outline-dark"><img src="/country/canada.png" alt="" srcset="">Canadian</button>
            <button @click="fetchFood('British')" type="button" class="btn btn-outline-dark"><img src="/country/british.png" alt="" srcset="">British</button>
            <button @click="fetchFood('Chinese')" type="button" class="btn btn-outline-dark"><img src="/country/china.png" alt="" srcset=""> Chinese</button>
            <button @click="fetchFood('French')" type="button" class="btn btn-outline-dark"><img src="/country/france.png" alt="" srcset="">French</button>
            <button @click="fetchFood('Indian')" type="button" class="btn btn-outline-dark"><img src="/country/india.png" alt="" srcset="">Indian</button>
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
        this.fetchFood('Canadian');
    },
    methods: {
        async fetchFood(Canadian) {
            try {
                const response = await this.$axios.get(`https://www.themealdb.com/api/json/v1/1/filter.php?a=${Canadian}`);
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
@click="fetchFood('Russian')"
@click="fetchFood('British')"
@click="fetchFood('Chinese')"
@click="fetchFood('French')" 
@click="fetchFood('Indian')" 