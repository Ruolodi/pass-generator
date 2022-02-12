<template>
  <div class="inputContainer form-control">
    <h1>Password generate</h1>
    <h1 v-if="errorCheck" style="color: red">
      Пожалуйста проверьте все ли поля были заполнены!
    </h1>
    <small> Введите текущий пароль </small>
    <input type="text" v-model.trim="oldPassword" />
    <small>Cгенерированный пароль:</small>
    <input type="text" v-model.trim="generatedPassword" />
    <button class="btn" @click="generate">Generate</button>
    <button class="btn" @click="save">Save</button>
    <button class="btn">Test</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      oldPassword: "",
      generatedPassword: "",
      errorCheck: false,
    }
  },
  methods: {
    save() {
      if (
        this.oldPassword.length === 0 &&
        this.generatedPassword.length === 0
      ) {
        this.errorCheck = true
      } else {
        this.passwords.push({
          old: this.oldPassword,
          generated: this.generatedPassword,
        })
      }
    },
    generate() {
      if (this.oldPassword.length === 0) {
        this.errorCheck = true
      } else {
        let oldLength = this.oldPassword.split("").length
        let arrCheck = this.oldPassword.split("")
        let arr_en = [
          "a",
          "b",
          "c",
          "d",
          "e",
          "f",
          "g",
          "h",
          "i",
          "j",
          "k",
          "l",
          "m",
          "n",
          "o",
          "p",
          "q",
          "r",
          "s",
          "t",
          "u",
          "v",
          "w",
          "x",
          "y",
          "z",
          "A",
          "B",
          "C",
          "D",
          "E",
          "F",
          "G",
          "H",
          "I",
          "J",
          "K",
          "L",
          "M",
          "N",
          "O",
          "P",
          "Q",
          "R",
          "S",
          "T",
          "U",
          "V",
          "W",
          "X",
          "Y",
          "Z",
        ]
        let arr_symb = ["!", ",", ".", "$", "%", "&", "?", "-", "+", "="]

        let arr_num = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]

        for (let i = 0; i < oldLength; i++) {
          if (!isNaN(arrCheck[i])) {
            arrCheck[i] = arr_num[Math.floor(Math.random() * 11)]
          } else {
            arrCheck[i] = arr_en[Math.floor(Math.random() * 53)]
          }
          this.generatedPassword = arrCheck.join("")
        }
      }
    },
  },
  watch: {
    oldPassword() {
      if (this.oldPassword.length > 0) {
        this.errorCheck = false
      }
    },
  },
  inject: ["passwords"],
}
</script>

<style></style>
