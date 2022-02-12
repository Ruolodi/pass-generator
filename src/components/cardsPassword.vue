<template>
  <div class="passwordCard" @click="check(id)">
    <h1>
      Старый пароль:
      <h2>{{ passwords[id].old }}</h2>
    </h1>
    <h1>
      Сгенерированный пароль:
      <h2>{{ passwords[id].generated }}</h2>
    </h1>
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
  },
}
</script>

<style></style>
