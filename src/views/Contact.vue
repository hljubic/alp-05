<template>
  <div>
    <h1>Kontakt</h1>

    <form>
      <br />

      <v-text-field
        label="Unesite ime i prezime.."
        hint="Ovo polje je obavezno"
        filled
      ></v-text-field>

      <v-text-field label="Unesite email.." filled></v-text-field>

      <v-file-input accept="image/*" label="Priloži datoteku" filled></v-file-input>

      <v-autocomplete
        label="Odaberi grad.."
        :items="['Mostar', 'Čapljina', 'Čitluk', 'Široki Brijeg']"
        filled
      ></v-autocomplete>

      <v-textarea
        label="Unesite poruku.."
        hint="Ovo polje je obavezno"
        filled
      ></v-textarea>
    </form>
  </div>
</template>

<script>
export default {
  name: "Contact",
};
</script>
