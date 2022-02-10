<template>
  <!-- <Header :value="value" :getValue="getValue"/> -->
  <!-- <input v-model="value" v-on:input="getValue" /> -->
  <!-- header -->
  <header>
    <div class="header">
      <List />
      <div class="search">
        <input
          type="text"
          id="search"
          placeholder="Поиск по названию картины"
          v-model="value"
        />
        <button id="btn" @click="getResult">Найти</button>
      </div>
    </div>
  </header>
  <!-- header -->
  <Modal v-if="modal" :modal="modal" :hide="hide" />
  <Main
    title="Картины эпохи Возрождения"
    :pictures="pictures"
    :buyCard="buyCard"
    :show="show"
  />
  <div v-if="basket.length !=0">
  <BasketContainer :basket="basket"/>
  </div>

  <Footer />
  
</template>

<script>
import Footer from "./layouts/footer.vue";
import Main from "./components/main.vue";
import List from "./components/list.vue";
import Modal from "./components/modal.vue";
import BasketContainer from './components/containerBasket.vue/basket.vue';


let DATA = [
        {
          id: 1,
          image: "./image/pic_1.png",
          title: "«Рождение Венеры» Сандро Боттичелли",
          price: "1 000 000",
          state: "Купить",
          strike_line: "2 000 000",
          sale: true,
        },
        {
          id: 2,
          image: "./image/pic_2.png",
          title: "«Тайная вечеря»  Леонардо да Винчи",
          price: "3 000 000",
          state: "Купить",
          sale: true,
        },
        {
          id: 3,
          image: "./image/pic_3.png",
          title: "«Сотворение Адама» Микеланджело",
          price: "5 000 000",
          state: "Купить",
          strike_line: "6 000 000",
          sale: true,
        },
        {
          id: 4,
          image: "./image/pic_4.png",
          title: "«Урок анатомии»  Рембрандт",
          price: "5 000 000",
          state: "В корзине",
          sale: false,
        },
      ];

export default {
  data() {
    return {
     
      pictures: JSON.parse(localStorage.getItem("pictures")) || DATA,
      value: "",
      basket: JSON.parse(localStorage.getItem("basket")) || [],
      modal: null,
    };
  },
  methods: {
    getResult: function () {
      let res = DATA.filter((i) => {
        return i.title
          .toLowerCase()
          .replace(/\s+/g, " ")
          .trim()
          .includes(this.value.replace(/\s+/g, " ").trim());
      });
      this.pictures = res;
      console.log(this.pictures);
     
    },
    
    buyCard: function (e) {
      setTimeout(() => {
        (this.pictures[e].state === "В корзине")
          ? (this.pictures[e].state = "Купить",  this.basket = this.basket.filter((i)=>{return i.title   !== this.pictures[e].title}),  console.log(this.basket))
          : (this.pictures[e].state = "В корзине", this.basket.push(this.pictures[e]), console.log(this.basket));
        localStorage.setItem("pictures", JSON.stringify(this.pictures));
           localStorage.setItem("basket", JSON.stringify(this.basket));
      }, 1000);
    },
    show: function (e) {
      this.modal = this.pictures[e];
      console.log(this.modal);
      console.log(e);
    },
    hide: function () {
      this.modal = null;
    },
  },

  name: "App",
  components: {
    Main,
    Footer,
    List,
    Modal,
    BasketContainer
  },
};

</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Merriweather", serif;
}
#app {
  height: 100vh;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
}
/* header */
header {
  border-bottom: 1px solid #e1e1e1;
  color: #343030;
  display: flex;
  justify-content: right;
  align-items: center;
}
.header {
  padding: 24px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 162px;
  width: 1216px;
  margin: 0 auto;
}
.list_content {
  display: flex;
  gap: 0px 48px;
  list-style-type: none;
  padding-left: 96px;
}
#search {
  width: 294px;
  height: 48px;
  border: 1px solid #e1e1e1;
  padding: 13px 16px;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 150%;
  color: #343030;
}
#search:hover,
#search:focus {
  outline: none;
  border: 1px solid #b5b5b5;
}
#btn {
  width: 122px;
  height: 48px;
  background: #403432;
  color: #ffffff;
  border: none;
  outline: none;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  line-height: 150%;
}
#btn:hover,
#btn:focus {
  background: #776763;
}
</style>
