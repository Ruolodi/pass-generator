<template>
  <div class="nav">
    <div class="blockBtn">
      <button class="btn" @click="switcher = !switcher">
        {{ switcher ? "Показать карточки" : "Скрыть карточки" }}
      </button>
    </div>
  </div>
  <input-ps></input-ps>
  <div v-if="switcher">
    <cards-password
      :passwords="passwords"
      v-for="(items, id) in passwords"
      :key="items"
      :id="id"
    ></cards-password>
  </div>
</template>

<script>
import cardsPasswordVue from "./components/cardsPassword.vue"
import inputPs from "./components/inputPs.vue"

export default {
  data() {
    return {
      switcher: true,
      passwords: [],
    }
  },
  components: {
    "input-ps": inputPs,
    "cards-password": cardsPasswordVue,
  },
  provide() {
    return {
      passwords: this.passwords,
    }
  },
}
</script>

<style></style>
