<template>
  <main>
  
    <div class="main">
      <h2>{{ title }}</h2>
      <div class="block_result">
        <div v-for="(item, index) in pictures" :key="index" class="card" >
          <div class="item" v-if="item.sale">
            <img :src="item.image" @click="show(index)"/>
            <div class="content">
              <p @click="show(index)">{{ item.title }}</p>
              <div class="price">
                <div class="price-text" v-if="item.strike_line">
                  <p id="strike_line">{{ item.strike_line }} $</p>
                  <p>{{ item.price }} $</p>
                </div>

                <div class="price-text" v-else>
                  <p>{{ item.price }} $</p>
                </div>
                <div v-if="item.state === 'Купить'">
                  <Buy :index="index" :buyCard="buyCard" />
                </div>
                <div v-if="item.state === 'В корзине'">
                  <Basket :index="index" :buyCard="buyCard" />
                </div>
              </div>
            </div>
          </div>
          <!--  -->
          <div class="item_disable" v-else>
            <div class="content_dis">
              <img :src="item.image" />
              <div class="content_disable">
                <p>{{ item.title }}</p>
                <div>Продана на аукционе</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Buy from "./buttons/buy.vue";
import Basket from './buttons/basket.vue';
// import Modal from './modal.vue';
export default {
  name: "Main",
  components: { Buy, Basket },
  props: {
    title: String,
    pictures: Array,
    buyCard: Function,
    show: Function
  },
};
</script>

<style scoped>
.main {
  padding: 45px 0;
  width: 1216px;
  margin: 0 auto;
}
.block_result {
  display: flex;
  margin: 39px auto;
  gap: 32px;
}
.card {
  border: 1px solid #e1e1e1;
  width: 280px;
  height: 328px;
}
.card > div > img {
  width: 100%;
  height: 160px;
}
.content {
  padding: 20px 24px;
  color: #343030;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 150%;
}
.price {
  margin-top: 22px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 150%;
}
#strike_line {
  color: #a0a0a0;
  text-decoration-line: line-through;
  font-style: normal;
  font-weight: 300;
  font-size: 14px;
  line-height: 150%;
}
/*  */
.item_disable {
  opacity: 0.5;
}
.item_disable > div > img {
  width: 100%;
}
.content_dis {
}
.content_disable {
  padding: 20px 24px;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 150%;
}
.content_disable > div {
  margin-top: 34px;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 150%;
  color: #343030;
}
</style>
