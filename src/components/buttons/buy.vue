<template>
  <button v-if="load"
    id="btn_buy"
    @click="
      buyCard(index);
      changeClass();
    "
  >
    Купить
  </button>
   <button class="btn_loader" v-if="!load">
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
  name: "Buy",
  components: {},
  props: { buyCard: Function, index: Number },
  methods: {
    changeClass: function () {
        this.load= false;
        // setTimeout(function(){this.load= true; console.log('will be true')}, 1000)
    },
  },
};
</script>
<style scoped>
#btn_buy {
  background: #382e2b;
  width: 118px;
  height: 48px;
  color: #f4f6f9;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  line-height: 150%;
  border: none;
  outline: none;
}
#btn_buy:hover,
#btn_buy:focus {
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
