<template>
  <div>
    <nuxt-link to="/login"><center>Buathong->click.</center></nuxt-link><br>
    <router-link :to="{ path: '/table1'}" replace><center>Register</center></router-link><br>
    <router-link :to="{ path: '/login'}" push><center>Register</center></router-link><br>
  </div>
</template>
<script>
export default {
  data() {
    return {
      id: 1,
    }
  },
}
</script>
