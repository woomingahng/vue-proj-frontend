<template>
  <div v-if="user">
    <h1>접속한 유저</h1>
    <p>아이디 : {{ user.id }}</p>
    <p>비밀번호 : {{ user.password }}</p>
    <p>이름 : {{ user.name }}</p>
    <router-link to="/index">아이스라떼</router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: null,
    }
  },
  created() {
    this.$http
      .get(`/getUser`)
      .then((res) => {
        const user = res.data.user
        if (user) this.user = user
      })
      .catch((err) => {
        console.log(err)
      })
  },
}
</script>

<style scoped></style>
