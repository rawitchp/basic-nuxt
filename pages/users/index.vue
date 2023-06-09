<template>
  <div>
    <p>USERS</p>
    <NuxtLink
      v-for="(user, i) in users.data"
      :key="i"
      class="card"
      :to="'/users/' + user.id"
    >
      <div>
        <img :src="user.avatar" width="70" height="70" />
      </div>
      <div>
        <div>ID: {{ user.id }}</div>
        <div>Fullname: {{ user.fname }} {{ user.lname }}</div>
        <div>Username: {{ user.username }}</div>
      </div>
    </NuxtLink>
  </div>
</template>

<script setup>
import { ref } from "vue";
import axios from "axios";
const users = ref([]);
async function getUsers() {
  try {
    users.value = await axios.get("https://www.melivecode.com/api/users");
  } catch (err) {
    console.log(err);
  }
}

getUsers();
</script>

<style lang="scss" scoped>
p {
  font-size: 30px;
  font-weight: 700;
}
.card {
  text-decoration: none;
  display: flex;
  gap: 20px;
  margin: 20px 20px;
  border: 1px solid lightgreen;
  background-color: lightgreen;
  color: azure;
  padding: 20px;
  border-radius: 5px;
  align-items: center;
}
.card:hover {
  background-color: rgb(45, 159, 45);
}
</style>