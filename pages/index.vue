<template>
  <div class="container">
<Nuxt-link to="./form" class="link">Связаться с нами</Nuxt-link>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.container {
  width: 100%;
  background-color:#E8EAF6;
min-height: 1000px;
padding-top: 400px;

}
.link{
  display: block;
  max-width:250px;
  margin:0 auto;
  color: black;
  padding: 20px 40px;
  text-align: center;
  text-decoration: none;
  background-color:#1DE9B6;
  border-radius: 10px;
  transition: .3s;
}
.link:hover{
  background-color:#004D40;
}
</style>
