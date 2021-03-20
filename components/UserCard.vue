<template>
  <div class="user-card" v-if="user">
    <img src="http://placehold.it/92x92" :alt="user.name" />
    <div class="user-card__content">
      <h3>{{ user.name }}</h3>
      <p>{{ user.about }}</p>
      <button @click="$emit('remove', user.id)">Remover</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserCard',
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped>
.user-card {
  background: #f1f1f1;
  box-shadow: 0 2px 3px 0 rgba(39, 39, 39, 0.116);
  padding: 15px;
  border-radius: 10px;
  margin: 15px 0;

  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}
.user-card img {
  margin-top: 15px;
  border-radius: 7px;
}
.user-card__content {
  padding: 15px;
  color: #4d4d4d;
}
.user-card__content h3 {
  font-size: 16px;
}
.user-card__content p {
  font-size: 13px;
  margin-top: 5px;
}
.user-card button {
  margin-top: 10px;
  cursor: pointer;
  padding: 10px;
  border-radius: 7px;
  border: 0;
  color: #f1f1f1;
  background: rgb(212, 55, 63);
  transition: filter 0.3s;
  box-shadow: 0 2px 3px 0 rgba(39, 39, 39, 0.116);
}
.user-card button:hover {
  filter: brightness(90%);
}
</style>
