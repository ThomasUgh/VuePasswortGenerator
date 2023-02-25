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
      <div>
        <input
          type="text"
          class="output"
          :value="password"
          placeholder="Passwort"
          readonly
        />
        <span class="copy" @click="copyToClipboard">📋</span>
      </div>
      <div>
        <input
        @click="generatePassword"
          type="button"
          class="create_password"
          value="Passwort erstellen"
        />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      passwordLength: 16, 
      includeUppercase: true,
      includeLowercase: true,
      includeSpecialChars: true,
      includeUmlauts: true,
      includeNumbers: true,
      password: "",
    };
  },
  methods: {
    generatePassword() {
      const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
      const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      const specialChars = "!§$%&/()=?+#-.,;:_";
      const umlauts = "äöüÄÖÜß";
      const numberChars = '0123456789';

      let allowedChars = "";
      if (this.includeUppercase) allowedChars += uppercaseChars;
      if (this.includeLowercase) allowedChars += lowercaseChars;
      if (this.includeSpecialChars) allowedChars += specialChars;
      if (this.includeUmlauts) allowedChars += umlauts;
      if (this.includeNumbers) allowedChars += numberChars;

      let password = "";
      for (let i = 0; i < this.passwordLength; i++) {
        const randomChar = allowedChars.charAt(
          Math.floor(Math.random() * allowedChars.length)
        );
        password += randomChar;
      }
      this.password = password;
    },
    copy() {
      const outputField = document.querySelector('input[type="text"]');
      outputField.select();
      document.execCommand('copy');
    }
  },
};
//Passwort stärken Check
//https://blog.logrocket.com/create-password-strength-checker-vue/
//https://www.npmjs.com/package/vue-password-strength-meter
//https://github.com/redsquirrelstudio/vue-password-checker
//
</script>

<style>
.copy {
  cursor: pointer;
  margin-left: 5px;
}

.create_password {
  width: 225px;
  border-radius: 15px;
  margin-top: 15px;
  display: inline-block;
  border: 1px solid #0096ff;
  background-color: #0096ff;
  color: #ffffff;
  padding: 8px 16px;
  transition: background-color 0.4s, color 0.4s;
}
.create_password:hover {
  background-color: transparent;
  color: #0096ff;
  cursor: pointer;
}
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
