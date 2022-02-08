<template>
  <button id="btn_basket" @click="buyCard(index);changeClass()"  v-if="load">В корзине</button>
   <button class="btn_loader" v-else>
      <div class="loader"></div>
    </button>
</template>
<script>
export default {
    data() {
    return {
      load: true,
    };
  },
  name: "Basket",
  components: {},
 props: { buyCard: Function, index: Number},
 methods: {
    changeClass: function () {
      this.load= false;
    },
  },
};
</script>
<style scoped>
#btn_basket {
  background: #5b3a32;
  content: "";
  width: 118px;
  height: 48px;
  color: #f4f6f9;
  border: none;
  outline: none;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  line-height: 150%;
}
#btn_basket:before {
  content: url("../../../public/image/VectorBtn.svg");
  margin-right: 7px;
}
#btn_basket:hover, #btn_basket:focus{
  background: #776763;
}
.btn_loader{
  background: #382e2b;
  width: 118px;
  height: 48px;
   border: none;
  outline: none;
}
.loader {
  margin: 0 auto;
background: white;
 width: 30px;
 height: 30px;
 border-radius: 50%;
 animation: load 3s linear;
}
@keyframes load{
  from{transform:rotateY(0deg)}
  to{transform: rotateY(1080deg);}
}
</style>
