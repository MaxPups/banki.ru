<template>
  <header>
    <div class="header">
      <List />
      <div class="search">
        <input
          type="text"
          id="search"
          placeholder="Поиск по названию картины"
          :value="value"
          @change="getValue"
        />
        <button id="btn" v-on:click="get()">Найти</button>
      </div>
    </div>
  </header>
</template>

<script>
import List from "../components/list.vue";
export default {
  data(){
    return {
      
    }
  },
  name: "Header",
  components: { List },
  props: { value: Array, getValue: Function },
  methods: {
    // get: () => {
    //   console.log('this event button');
    // },
    // getChange: ()=>{
    //         console.log('this event input');
    // }
  },
};
</script>

<style scoped>
header {
  border-bottom: 1px solid #e1e1e1;
  color: #343030;
  display: flex;
  justify-content: right;
  align-items: center;
}
.header {
  padding: 24px 0;
  padding-left: 92px;
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
