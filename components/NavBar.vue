<template>
  <section class="nav_bar">
    <header class="row">
      <nuxt-link class="col logo_link" to="/">
        <div class="log">
          <h3>C</h3>
          <div class="log_text">
            <h3>COOKING</h3>
          </div>
        </div>
      </nuxt-link>
      <div class="col search">
        <div class="search_result">
          <input class="search_result_input" v-model="food_search" @input="fetchData" type="search" placeholder="No Search" />
          <ul class="search_list" v-for="item of food_search_result" :key="item.id">
            <li v-if="showSearchResult">
              <nuxt-link :to="`/${item.idMeal}`" @click.native="resultSelect"><img :src="item.strMealThumb" alt=""
                  srcset="" /><span>{{
                    item.strMeal
                  }}</span></nuxt-link>
            </li>
          </ul>
        </div>
      </div>
    </header>
  </section>
</template>

<script>
export default {
  data() {
    return {
      food_search: null,
      food_search_result: [],
      empty_search_result: [],
      showSearchResult: true,
    };
  },
  created() {
    this.fetchData();

  },

  methods: {
    async fetchData() {
      const response = await this.$axios.get(
        `https://www.themealdb.com/api/json/v1/1/search.php?s=${this.food_search}`
      );
      let doit = response.data;

      console.log(doit.meals);
      if (this.food_search === "" || doit.meals === null) {
        this.food_search_result = [];
      } else {
        this.food_search_result = doit.meals.slice(0, 4);
        this.showSearchResult = doit.meals ? true : false;
      }
    },
    resultSelect() {
      this.food_search = "";
      this.showSearchResult = false;
    },
    onFocusOut() {
      window.addEventListener('keypress', (e) => {
        if (e.key === 'Escape')
          this.food_search = "";
      })

    }

  },
};
</script>

<style lang="scss">
.nav_bar {


  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1em;

    .logo_link {
      text-decoration: none;

      .log {
        display: flex;
        align-items: center;
        text-decoration: none;
      }

      .log h3:last-child {
        color: #e24538;
      }

      .log>h3 {
        width: 80px;
        height: 80px;
        background-color: #e24538;
        border-radius: 50%;
        color: #fff;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-right: 10px;
      }
    }

    img {
      max-width: 120px;
      min-height: 51px;
    }

    .search {
      display: flex;
      justify-content: flex-end;

      .search_result {
        background-color: #f7f7f7cc;
        position: absolute;
        top: -1em;
        z-index: 10;

        input {
          border: none;
          min-width: 300px;
          height: 40px;
          padding: 10px;
          border: 1px solid #d8d8d8;
          background-color: #f7f7f7cc;
          &:focus{
            outline: none;
          }
        }
        
        .search_list {
          li {
            background-color: #f7f7f7cc;
            border: 1px solid #d8d8d8;
            list-style: none;
            width: 300px;
            display: block;
            padding: -1em;
            margin-bottom: -.5em;

            a {
              display: flex;
              text-decoration: none;

              img {
                width: 150px;
              }

              span {
                color: #e24538;
                font-weight: 700;
                margin-left: 1em;
                margin-top: 1em;
              }
            }
          }
        }

      }
    }
  }
}
</style>
