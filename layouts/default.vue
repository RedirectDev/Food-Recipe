<template>
  <div class="container-xl">
    <NavBar />
    <nuxt />
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss">
*,
::before,
::after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}


body {
  background-image: url('/background_img.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
 
}
</style>