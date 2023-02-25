<template>
  <section class="passwordgenerator">
    <h1 class="title">Passwort Generator V1</h1>
    <div class="ui">
      <div class="pw_input">
        <input
          type="number"
          class="pw_length"
          v-model.number="passwordLength" min="6" max="99"
          placeholder="Passwortlänge"
        />
      </div>
      <div class="checkboxen">
        <div class="checkbox_buchstaben">
          <input
            type="checkbox"
            class="check"
            v-model="includeLowercase"
            checked
          /><label class="text"> Kleinbuchstaben</label>
          <input
            type="checkbox"
            class="check"
            v-model="includeUppercase"
            checked
            value="on"
          /><label class="text"> Großbuchstaben</label>
          <input
            type="checkbox"
            class="check"
            v-model="includeUmlauts"
            checked
          /><label class="text"> Umlaute</label>
        </div>

        <div class="checkbox_zahlen">
          <input
            type="checkbox"
            class="check"
            v-model="includeNumbers"
            checked
          /><label class="text"> Nummern</label>
          <input
            type="checkbox"
            class="check"
            v-model="includeSpecials"
            checked
          /><label class="text"> Sonderzeichen</label>
        </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "HelloWorld",
  methods: {},
};
//Passwort stärken Check
//https://blog.logrocket.com/create-password-strength-checker-vue/
//https://www.npmjs.com/package/vue-password-strength-meter
//https://github.com/redsquirrelstudio/vue-password-checker
//
</script>

<style>
.title {
}

.pw_length {
  border-radius: 5px;
  width: 160px;
}

.text {
  margin-bottom: 10px;
}

.checkboxen {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}
.ui {
  display: flex;
  flex-direction: column;
}

.checkbox_buchstaben {
  margin-right: 25px;
  display: flex;
  flex-direction: column;
}

.checkbox_zahlen {
  display: flex;
  flex-direction: column;
}
</style>
