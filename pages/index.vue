<template>
  <div class="container">
    <div class="container-content">
      <UserCard
        v-for="user in users"
        :key="user.id"
        :user="user"
        @remove="removeUser"
      />
    </div>
    <div class="container-count">{{ users.length }} Usuários</div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data: () => ({
    users: [],
  }),
  async fetch() {
    this.users = await fetch('https://adjonata.github.io/json/users.json')
      .then((response) => response.json())
      .catch((error) => console.error(error))
  },
  methods: {
    removeUser(index) {
      this.users.splice(index, 1)
    },
  },
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: none;
  background: #f1f1f1;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.container-content {
  width: 600px;
  padding: 30px 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.container-count {
  position: fixed;
  top: 35px;
  right: 35px;
  color: #353535;
  font-weight: bold;
}
</style>
