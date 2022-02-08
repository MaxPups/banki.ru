<template>
  <footer>
    <div class="footer">
      <List />
      <Contacts/>
    </div>
  </footer>
</template>

<script>
import List from "../components/list.vue";
import Contacts from '../components/contacts.vue';
export default {
  name: "Footer",
  components: {
    List, Contacts
  },
  props: {},
};
</script>

<style scoped>
.footer {
  padding: 37px 0;
  background: #eceaea;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #555555;
  gap: 150px;
}

</style>
