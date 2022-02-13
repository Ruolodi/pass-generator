<template>
  <div class="passwordCard">
    <h1>
      Старый пароль:
      <h2>{{ passwords[id].old }}</h2>
    </h1>
    <h1>
      Сгенерированный пароль:
      <h2>{{ passwords[id].generated }}</h2>
    </h1>
    <button class="btnPassCard" @click="deletePass(id)">Удалить карту</button>
  </div>
</template>

<script>
export default {
  props: ["items", "passwords", "id"],
  data() {
    return {}
  },
  methods: {
    check(id) {
      console.log(this.passwords[id])
    },
    deletePass(id) {
      this.passwords.splice(id, 1)
    },
  },
}
</script>

<style></style>
