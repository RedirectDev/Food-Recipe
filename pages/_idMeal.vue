
<template>
    <section>
        <div v-for="meal in response" :key="meal.id" class="food_page">
            <h3> {{ meal.strMeal }}</h3>

            <div class="food_info row">
                <img class=" food_img" :key="meal.id" :src="meal.strMealThumb" alt="" srcset="" />
                <div class=" engredients">
                    <h5>Engredients:</h5>
                    <ul class="engredients_list">
                        <li>{{ meal.strIngredient1 }}</li>
                        <li>{{ meal.strIngredient2 }}</li>
                        <li>{{ meal.strIngredient3 }}</li>
                        <li>{{ meal.strIngredient4 }}</li>
                        <li>{{ meal.strIngredient5 }}</li>
                        <li>{{ meal.strIngredient6 }}</li>
                        <li>{{ meal.strIngredient7 }}</li>
                        <li>{{ meal.strIngredient8 }}</li>
                        <li>{{ meal.strIngredient9 }}</li>
                        <li>{{ meal.strIngredient10 }}</li>
                    </ul>
                </div>
            </div>
            <div>Today you will cook {{ meal.strCategory }} with {{ meal.strArea }} recipe. {{ meal.strInstructions }}
            </div>
        </div>
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
            const response = await this.$axios.get(`https://www.themealdb.com/api/json/v1/1/lookup.php?i=${this.$route.params.idMeal}`);
            let doit = response.data;
            this.response = doit.meals;
        } catch (error) {
            console.log(error);
        }
    },
};
</script>

<style lang="scss">
.food_page {
    margin-top: 1em;

    h3 {
        margin: 1em;
        display: flex;
        justify-content: center;
        align-content: center;
        align-items: center;
    }

    .food_info {
        margin-bottom: 1em;
        .engredients {
            h5 {
                color: #e24538;
                margin-left: 1em;
                margin-bottom: 1em;
            }

            .engredients_list {
               
                li {
                    list-style: none;
                    margin-left: 1.3em;
                }
            }
        }
    }

    .food_img {
        border-radius: 1em;
        width: 300px;
        height: 300px;
        margin: 0 1em;
    }
}</style>