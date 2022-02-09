<template>
  <div class="container">
    Корзина <img src="https://img.icons8.com/material-outlined/15/000000/shopping-basket-star.png"/> :
    <ul>
      <li v-for="(item, index) of this.basket" :key="index">{{ item.title }}/{{item.price}}$</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "BasketContainer",
  components: {},
  props: { basket: Array },
};
</script>
<style scoped>
.container{
    border-top: 1px solid black;
     /* border-radius: 8px; */
    margin: 0 auto;
    overflow-y: auto;
    padding: 0px 30px;
    padding-bottom: 10px;
     width: 1216px;
}
ul{
    list-style-type: none;
    display: flex;
        /* justify-content: space-between; */
    gap: 15px;
    margin-top: 5px;
}
li{
    font-size: 0.7vw;
}
li::after{
    content: ""
}
</style>
