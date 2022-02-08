<template>
  <div class="list_box">
    <ul class="list_content">
      <li><a href="#">Каталог</a></li>
      <li><a href="#">Доставка</a></li>
      <li><a href="#">Оплата</a></li>
      <li><a href="#">Контакты</a></li>
      <li><a href="#">О компании</a></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "List",
  props: {},
};
</script>
<style scoped>
a {
  text-decoration: none;
  color: inherit;
}
a:hover,
a:focus {
  border: none;
  outline: none;
  opacity: 0.5;
}
.list_content {
  display: flex;
  gap: 0px 48px;
  list-style-type: none;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 150%;
}
</style>
