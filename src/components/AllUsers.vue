<template>
  <div>
    <p v-for="(user, i) in users" :key="i">{{ user.first_name }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      users: undefined,
    };
  },
  mounted() {
    axios
      .request({
        url: `https://reqres.in/api/users`,
      })
      .then((response) => {
        console.log(`got data`);
        this.users = response.data.data;
      })
      .catch((error) => {
        console.log(`error${error}`);
      });
  },
};
</script>

<style scoped>
</style>