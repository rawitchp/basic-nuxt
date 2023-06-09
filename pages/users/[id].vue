<template>
  <div>
    <div>ID: {{ data.id }}</div>
    <div><img :src="data.avatar" /></div>
    <div>Fullname: {{ data.fname }} {{ data.lname }}</div>
    <div>Username: {{ data.username }}</div>
    <div>Email: {{ data.email }}</div>
    <button @click="() => router.back()">Back</button>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
const data = ref({});
const route = useRoute();
const router = useRouter();
console.log(route.params.id);
async function getData() {
  try {
    data.value = await axios
      .get(`https://www.melivecode.com/api/users/${route.params.id}`)
      .then((raw) => raw.data.user);
  } catch (err) {
    console.log(err);
  }
}
getData();
</script>

<style lang="scss" scoped>
</style>