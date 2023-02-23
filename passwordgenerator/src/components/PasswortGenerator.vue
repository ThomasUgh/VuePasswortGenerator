<template>
  <section class="passwordgenerator">
    <h1 class="title">Passwort Generator V1</h1>
    <div class="ui">
      <div class="pw_input">
        <input type="number" class="pw_length" value="16" placeholder="Passwortlänge">
      </div>
      <div class="checkbox_buchstaben">
        <input type="checkbox" id="lowercase" checked value="on"><span class="text"> Kleinbuchstaben</span>
        <input type="checkbox" id="upperrcase" checked value="on"><span class="text"> Großbuchstaben</span>
        <input type="checkbox" id="umlauts" checked value="on"><span class="text"> Umlaute</span>
      </div>

      <div class="checkbox_zahlen">
        <input type="checkbox" id="numbers" checked value="on"><span class="text"> Nummern</span>
        <input type="checkbox" id="special" checked value="on"><span class="text"> Sonderzeichen</span>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: 'HelloWorld',
  methods: {
  },
}
</script>

<style>
.title {}

.ui {}

.checkbox_buchstaben {}

.checkbox_zahlen {}
</style>
