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
    <button class="btn" @click="generate(false)">Generate</button>
    <button class="btn" @click="generate(true)">
      Generate strong password
    </button>
    <button class="btn" @click="save">Save</button>
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
        this.errorCheck = trueФ
      } else {
        this.passwords.push({
          old: this.oldPassword,
          generated: this.generatedPassword,
        })
      }
    },
    generate(strong) {
      //strong получает булевое и генерация происходит с добавлением спец символов при TRUE
      let arrCheck = []
      if (this.oldPassword.length === 0) {
        //Проверка на пустое поле и заполнение в случае true
        for (let i = 0; i < 8; i++) {
          switch (Math.floor(Math.random() * 3)) {
            case 0:
              arrCheck[i] = String.fromCharCode(
                Math.floor(Math.random() * (90 - 65) + 65)
              )
              break
            case 1:
              arrCheck[i] = String.fromCharCode(
                Math.floor(Math.random() * (122 - 97) + 97)
              )
              break
            case 2:
              arrCheck[i] = String.fromCharCode(
                Math.floor(Math.random() * (57 - 48) + 48)
              )
              break
          }
        }
        this.oldPassword = arrCheck.join("")
      }
      let oldLength = this.oldPassword.split("").length
      arrCheck = this.oldPassword.split("")
      /* let arr_symb = ["!", ",", ".", "$", "%", "&", "?", "-", "+", "="] */

      for (let i = 0; i < oldLength; i++) {
        if (strong && !Math.floor(Math.random() * 3)) {
          //проверка на сложность пароля, и вероятность выдать спецсимволы 33 процента из-за !
          arrCheck[i] = String.fromCharCode(
            Math.floor(Math.random() * (47 - 33) + 33)
          )
        } else {
          if (!isNaN(arrCheck[i])) {
            arrCheck[i] = String.fromCharCode(
              //ASCII таблица
              Math.floor(Math.random() * (57 - 48) + 48) //рандомит номер символа в выбранном диапазоне
            ) //рандом чисел в строке
          } else {
            if (Math.floor(Math.random() * 2)) {
              arrCheck[i] = String.fromCharCode(
                Math.floor(Math.random() * (90 - 65) + 65)
              ) //рандом больших букв английского алфавита
            } else {
              arrCheck[i] = String.fromCharCode(
                Math.floor(Math.random() * (122 - 97) + 97)
              ) //рандом маленьких букв английского алфавита
            }
          }
        }
        this.generatedPassword = arrCheck.join("")
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
