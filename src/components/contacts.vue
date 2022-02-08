<template>
  <div class="block_contacts">
    <div id="phone">
      <a href="#"> +7 (812) 555-55-55 </a>
    </div>
    <div id="map">г. Санкт-Петербург, ул. Ефимова, 3</div>
  </div>
</template>
<script>
export default {
  name: "Contacts",
  props: {},
};
</script>
<style scoped>
.block_contacts {
  display: flex;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 150%;
  color: inherit;
  gap: 75px;
}
#phone {
  content: "";
  position: relative;
}
#phone > a {
  text-decoration: none;
  color: inherit;
}
#phone:before {
  content: url("../../public/image/Group 56.png");
  /* margin-right: 9px; */
  position: absolute;
  top: 15%;
  left: -20px;
}
#map {
  content: "";
  position: relative;
}
#map:before {
  content: url("../../public/image/adress.svg");
  /* margin-right: 11px; */
  position: absolute;
  top: 15%;
  left: -21px;
}
</style>