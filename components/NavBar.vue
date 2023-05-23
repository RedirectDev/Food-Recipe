<template>
  <header class="row">
    <div class="log">
      <h3>C</h3>
      <div class="log_text"><h3>COOKING</h3></div>
    </div>
    <div class="search"><input type="search" name="" id="" /></div>
    <div class="fav">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="40"
        height="40"
        fill="#e24538"
        class="bi bi-heart-fill"
        viewBox="0 0 16 16"
      >
        <path
          fill-rule="evenodd"
          d="M8 1.314C12.438-3.248 23.534 4.735 8 15-7.534 4.736 3.562-3.248 8 1.314z"
        />
      </svg>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss">
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 1em;
  .log {
    display: flex;
    align-items: center;
  }
  img {
    max-width: 120px;
    min-height: 51px;
  }

  .log h3:last-child {
    color: #e24538;
  }
  .log > h3 {
    width: 80px;
    height: 80px;
    background-color: #e24538;
    border-radius: 50%;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right:10px ;
  }
  .search {
    input {
      border: none;
      min-width: 500px;
      height: 40px;
      border-radius: 25px;
      border: 1px solid #d8d8d8;
      background-color: #f7f7f7cc;
    }
  }
}
</style>